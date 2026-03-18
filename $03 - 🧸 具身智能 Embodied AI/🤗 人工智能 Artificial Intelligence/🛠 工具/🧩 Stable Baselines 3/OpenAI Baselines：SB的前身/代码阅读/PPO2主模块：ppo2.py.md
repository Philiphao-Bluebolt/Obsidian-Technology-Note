这个是Baselines PPO2算法的核心模块，主要包含一个`learn`函数

```python
def learn(*, 
		  network, 
		  env, 
		  total_timesteps, 
		  eval_env = None,
		  seed=None, 
		  nsteps=2048, 
		  ent_coef=0.0, 
		  lr=3e-4,
		  vf_coef=0.5, 
		  max_grad_norm=0.5, 
		  gamma=0.99, 
		  lam=0.95,
		  log_interval=10, 
		  nminibatches=4, 
		  noptepochs=4, 
		  cliprange=0.2,
		  save_interval=0, 
		  load_path=None, 
		  model_fn=None, 
		  **network_kwargs)
```

下面主要是`learn`函数的分析

---
## 输入参数分析

OpenAI在这里留了很大一段注释解释每个输入参数的含义

| 英文                | 中文              | 类型                 | 解释                                                                                        |
| ----------------- | --------------- | ------------------ | ----------------------------------------------------------------------------------------- |
| `network`         | 策略神经网络          | `function`         | 一个描述了策略（Policy）神经网络结构的函数，接收`tf`张量作为输入，输出一个张量。可以用字符串调用`baselines.common/models.py`模块里现成的网络 |
| `env`             | 向量化训练环境         | `VecEnv`           | 为并行训练准备的向量化环境，应该只能用于Gym和Mujoco等虚拟环境                                                       |
| `total_timesteps` | 总步数             | `int`              | 环境中执行的（最大？）步数                                                                             |
| `eval_env`        | 向量化测试环境         | `VecEnv`           | 测试环境用于测试强化学习模型的表现                                                                         |
| `seed`            | 预设随机种子          | `int`              | 用于生成随机数的一个预设种子，会输入到`set_global_seeds`函数用于生成种子                                             |
| `nsteps`          | 更新网络间隔步数        | `int`              | 在向量化环境中每执行`nsteps`步（Step）更新一次网络，因此推断一个Batch包含`nsteps`个经验                                  |
| `ent_coef`        | 策略熵系数           | `float`            | 用于控制策略优化的随机程度（Stochastics），即倾向于探索（Exploration）的程度                                         |
| `lr`              | 学习率             | `function`或`float` | 控制网络优化速度（梯度下降速度）的系数，可以是一个固定值，也可以是一个随训练过程变化（一般是减小）的函数                                      |
| `vf_coef`         | 价值函数损失系数        | `float`            |                                                                                           |
| `max_grad_norm`   | 最大梯度阈值          | `float`            | 限制网络反向传播最大梯度值（范数）的阈值                                                                      |
| `gamma`           | 折扣因子            | `float`            | 取值范围为$[0,1]$，用于描述计算未来奖励（Reward）时的衰减系数，直观上，Gamma取值越小，策略越倾向于考虑短期奖励                          |
| `lam`             |                 | `float`            |                                                                                           |
| `log_interval`    | 日志记录间隔          | `int`              | 每两次记录日志之间间隔的步数                                                                            |
| `nminibatches`    | 网络更新Minibatch容量 | `int`              | 决定了一次输入网络的经验（Experiences）的个数                                                              |
| `noptepochs`      |                 | `int`              |                                                                                           |
| `cliprange`       |                 | `float`或`function` |                                                                                           |
| `save_interval`   | 保存步数间隔          | `int`              | 决定多少步（Step）才保存一次模型                                                                        |
| `load_path`       | 模型导入路径          | `str`              | 用于读取文件，导入已有的模型Checkpoint                                                                  |
| `model_fn`        |                 | `str`              |                                                                                           |
| `network_kwargs`  |                 |                    |                                                                                           |

---
## 生成随机数种子

```python
set_global_seeds(seed)
```

这个函数的原型位于`baselines.common`的`misc_util.py`文件中

```python
def set_global_seeds(i):
    try:
        import MPI
        rank = MPI.COMM_WORLD.Get_rank()
    except ImportError:
        rank = 0

    myseed = i  + 1000 * rank if i is not None else None
    try:
        import tensorflow as tf
        tf.random.set_seed(myseed)
    except ImportError:
        pass

    np.random.seed(myseed)
    random.seed(myseed)
```

函数利用输入的初始种子和MPI分布式运算的序号`rank`生成随机种子，给`random`、`numpy`、`tensorflow`模块生成随机数用

---
## 类型转换：`lr`、`cliprange`、`total_timesteps`

这里是对学习率`lr`、`cliprange`、总步数`total_timesteps`的类型检测与转换

```python
if isinstance(lr, float): lr = constfn(lr)
else: assert callable(lr)

if isinstance(cliprange, float): cliprange = constfn(cliprange)
else: assert callable(cliprange)

total_timesteps = int(total_timesteps)
```

如果传入的学习率`lr`和`cliprange`的一个（常值）浮点数，就调用`constfn`函数将其变成一个常值函数。

`constfn`函数的作用就是输出常值函数，其具体实现也位于`ppo2.py`文件内

```python
def constfn(val):
    def f(_):
        return val
    return f
```

---
## 获取神经网络

```python
if isinstance(network, str):
	network_type = network
	policy_network_fn = get_network_builder(network_type)(**network_kwargs)
	network = policy_network_fn(ob_space.shape)
```

这里根据传入的`network`字符串参数返回一个相应的`tf.keras.Model`神经网络给`network`，主要的实现函数位于`baselines.common.models`（`models.py`文件）

`get_network_builder()`会返回一个在`model.py`中已注册的网络构建函数，网络构建函数接收观察空间的形状即返回网络

```python
def get_network_builder(name):
    if callable(name):
        return name
    elif name in mapping:
        return mapping[name]
    else:
        raise ValueError('Unknown network type: {}'.format(name))
```

---
## 计算Batch和训练输入次数

```python
nbatch = nenvs * nsteps
nbatch_train = nbatch // nminibatches
```

这里的`nbatch`指的是网络更新时Batch收集到的经验的个数，数值上等于上次更新到现在的步数乘以环境副本的个数

超参数`nminibatches`是更新时一次输入网络的经验个数，因此计算出的`nbatch_train`表示更新一次需要输入的次数（即Minibatch的数量）

---
## 生成模型对象

```python
if model_fn is None:
	from baselines.ppo2.model import Model
	model_fn = Model

model = model_fn(ac_space=ac_space, 
				 policy_network=network, 
				 ent_coef=ent_coef, 
				 vf_coef=vf_coef,
				 max_grad_norm=max_grad_norm)
```

如果没有指定`model_fn`，就从`baselines.ppo2.model`导入默认的`Model`类并用这个`Model`类指定一个模型对象`model`

模型是非常重要的，因为模型包含了最底层的运算以及网络优化的算法

如果导入了之前保存的训练过的模型，则通过Tensorflow的Checkpoint功能导入并恢复

```python
if load_path is not None:
    load_path = osp.expanduser(load_path)
    ckpt = tf.train.Checkpoint(model=model)
    manager = tf.train.CheckpointManager(ckpt, load_path, max_to_keep=None)
    ckpt.restore(manager.latest_checkpoint)
```

---
## 创建`Runner`对象

```python
runner = Runner(env=env, 
				model=model, 
				nsteps=nsteps, 
				gamma=gamma, 
				lam=lam)
				
if eval_env is not None:
    eval_runner = Runner(env = eval_env, 
					     model = model,
					     nsteps = nsteps, 
					     gamma = gamma, 
					     lam= lam)

epinfobuf = deque(maxlen=100)

if eval_env is not None:
	eval_epinfobuf = deque(maxlen=100)
```

按照注释的说法，这里的`Runner`对象用于从batch里切分出Minibatch，如果有输入测试环境`eval_env`则为测试环境也创建一个对象

`Runner`类的定义在`ppo2/runner.py`文件中，继承了一个`common/runners.py` 的`AbstractEnvRunner`类



---
## 计算网络更新次数

```python
nupdates = total_timesteps//nbatch
```

网络更新次数