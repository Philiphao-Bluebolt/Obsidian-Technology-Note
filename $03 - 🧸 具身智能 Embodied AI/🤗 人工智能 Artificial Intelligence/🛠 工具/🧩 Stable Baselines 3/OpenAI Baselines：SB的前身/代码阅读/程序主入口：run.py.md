OpenAI Baselines算法的主入口位于`run.py`中

```python
if __name__ == '__main__':
    main(sys.argv)
```

[[#通用库调用]]
[[#Baselines内部库调用]]
[[#函数]]
[[#内部函数调用逻辑图——PPO2]]

---
## 通用库调用

| 库或模块                    | 缩写  | 用途                           |
| ----------------------- | --- | ---------------------------- |
| sys                     |     | 访问操作系统相关参数，获取命令行输入参数以及操作系统类型 |
| re                      |     | 处理正则表达式                      |
| multiprocessing         |     | 多进程并行执行代码，提高性能               |
| os.path                 | osp | 文件路径处理                       |
| gym                     |     | 强化学习的环境，作为代码的示例              |
| collections.defaultdict |     | 更好用的字典，避免访问到不存在的key          |
| tensorflow              | tf  | 开源机器学习编程框架                   |
| numpy                   | np  | 通用线性代数库，提供矩阵和向量运算支持          |
| importlib.import_module |     | 提供在程序运行时动态导入库和模块的支持          |

---
## Baselines内部库调用

| 模块                 | 源文件                                         | 类型  | 用途           |
| ------------------ | ------------------------------------------- | --- | ------------ |
| VecFrameStack      | baselines.common.vec_env                    |     |              |
| VecNormalize       | baselines.common.vec_env                    |     |              |
| VecEnv             | baselines.common.vec_env                    |     | 向量化环境的类      |
| VecVideoRecorder   | baselines.common.vec_env.vec_video_recorder |     |              |
| common_arg_parser  | baselines.common.cmd_util                   | 函数  | 命令行已知参数读取    |
| parse_unknown_args | baselines.common.cmd_util                   | 函数  | 命令行未知参数提取及储存 |
| make_vec_env       | baselines.common.cmd_util                   | 函数  |              |
| make_env           | baselines.common.cmd_util                   | 函数  |              |
| logger             | baselines.logger                            | 模块  | 运行日志记录       |

---
## 函数

| 函数名                         | 中文名               | 用途                                                                                |
| --------------------------- | ----------------- | --------------------------------------------------------------------------------- |
| train                       | 训练入口函数            | 获取并调用各算法的`learn()`函数、调用环境创建函数`build_env()`；返回训练好的模型以及环境                           |
| build_env                   | 环境创建函数            | 判断CPU内核数量，调用函数`make_env()`或者`make_vec_env()`创建环境                                  |
| get_env_type                | 环境类型读取函数          | 在未指定环境类型`env_type`时通过环境ID`env_id`返回环境类型                                           |
| get_default_network         | 默认网络（字符串）获取函数     | 在未指定神经网络类型`network`时返回一个默认的网络类型字符串，除`atari`和`retro`以外的环境均默认使用`mlp`网络              |
| get_alg_module              | 算法模块获取函数          | 根据输入的算法类型调用`importlib`库载入相应的模块，返回代表这个模块的类                                         |
| get_learn_function          | `learn`函数获取函数     | 根据输入的算法类型调用`get_alg_module()`函数获取算法模块里的`learn()`函数                                |
| get_learn_function_defaults | `learn`函数默认参数获取函数 | 根据输入的算法和环境类型调用`get_alg_module()`函数获取各算法模块里输入到`learn()`函数的默认参数（存放在`default.py`文件中） |
| parse_cmdline_kwargs        |                   |                                                                                   |
| configure_logger            |                   |                                                                                   |
| main                        | 主入口函数             | 拆分读取命令行参数、调用训练入口函数`train()`、保存模型、展示训练效果（输入`play`参数时）                              |

---
## 内部函数调用逻辑图

箭头表示调用关系，红色是最重要的函数，黄色是次重要的函数，蓝色是`run.py`文件中的其他函数，绿色是`common`模块的函数

![[Baselines_run.png]]

---
## 命令行参数处理：`common_arg_parser()`



---
## 

