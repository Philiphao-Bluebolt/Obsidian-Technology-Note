由于OpenAI Baseline发布于2018年，当时用到的很多Python库已经更新了很多个版本，有些库需要降低版本才能使代码正确运行

配制主要步骤参考`README.md`

下面是一些配置的报错和解决方案，可供参考

---
## 使用兼容TensorFlow2的版本

主分支`master`版本使用TensorFlow1编写，而现在TensorFlow的默认最新版本是TensorFlow2，两代之间并不兼容，因此需要下载`tf2`分支版本才能用TensorFlow2运行

![[Pasted image 20240415153033.png]]

---
## 过时类型`np.bool`

+ 报错信息：“`np.bool` was a deprecated alias for the builtin `bool`”

线性代数库`numpy`在`1.20.0`版本开始不再支持`np.bool`类型，需要在源码中找出所有用到的`np.bool`并修改为`bool`，官方特别声明这个修改不会影响运行

---
## 无法导入`FlattenDictWrapper`

+ 报错信息：“ImportError: cannot import name `FlattenDictWrapper` from `gym.wrappers`”
+ Github讨论：[https://github.com/openai/baselines/issues/1129](https://github.com/openai/baselines/issues/1129)

需要将Gym的版本降低到`0.14`以下

![[Pasted image 20240415154545.png]]

---
## 连接超时无法下载Gym

+ 报错信息：“TimeoutError: The read operation timed out”
+ 解决方案：[强化学习环境Gym 旧版本下载](https://blog.csdn.net/qq_49696822/article/details/135611583?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171323804816800222879229%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171323804816800222879229&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-135611583-null-null.142^v100^pc_search_result_base2&utm_term=gym%E4%B8%8B%E8%BD%BD&spm=1018.2226.3001.4187)

`pip`命令可以指定连接超时阈值、下载版本和下载源

```bash
pip  --default-timeout=100  install  gym=0.13.0  -i https://pypi.tuna.tsinghua.edu.cn/simple
```

---
## 找不到属性`entry_point`

+ 报错信息：“AttributeError: `EnvSpec` object has no attribute `entry_point`”
+ Github讨论：[https://github.com/openai/baselines/issues/977](https://github.com/openai/baselines/issues/977)

由于Gym的版本降低了，所以需要将`entry_point`改为`_entry_point`

---
## 缺少cv2模块

+ 报错信息：“No module named cv2”

这里需要安装OpenCV，安装方法和安装Gym差不多

```bash
pip  --default-timeout=100  install  opencv-python  -i https://pypi.tuna.tsinghua.edu.cn/simple
```

---
## Cloudpickle和Multiprocessing出错

+ 报错信息：

```bash
File "/home/bluebolt/anaconda3/lib/python3.11/site-packages/cloudpickle/cloudpickle.py", line 212, in <setcomp>
    out_names = {names[oparg] for _, oparg in _walk_global_ops(co)}
                 ~~~~~^^^^^^^
IndexError: tuple index out of range
```

```bash
File "/home/bluebolt/anaconda3/lib/python3.11/multiprocessing/process.py", line 148, in join
    assert self._popen is not None, 'can only join a started process'
           ^^^^^^^^^^^^^^^^^^^^^^^
AssertionError: can only join a started process
```

Cloudpickle是一个集群运算库，支持多进展多计算机执行程序，Multiprocessing是一个用于多进程执行的库

---