### Stable Baselines 3 (2022)

+ Github：[Stable-Baselines-3](https://github.com/DLR-RM/stable-baselines3)
+ 文档：[Stable Baselines3](https://stable-baselines3.readthedocs.io/en/master/)

Stable Baselines 3是在OpenAI Baselines基础上改进的开源强化学习算法框架，由德国航天航空局于2022年发布并负责维护，提供了完善的文档以及Pypi库以供调用，使用PyTorch编写

```bash
pip  install  stable-baselines3[extra]
```

Stable Baselines 3支持的算法包括A2C、DDPG、DQN、PPO、HER、SAC

Stable Baselines 3的接口兼容Gymnasium的环境，自定义的环境则需要根据Gymnasium自定义环境的格式来编写

+ 文档：[Using Custom Environments](https://stable-baselines3.readthedocs.io/en/master/guide/custom_env.html)

实际上这已经是第三代Stable Baselines算法，之前的一代及二代Stable Baselines算法仍基于Tensorflow，现已停止维护

+ Github（一代）：[Stable-Baselines](https://github.com/hill-a/stable-baselines)

### 参考课程

+ SB3简明教程：[StableBaselines3强化学习框架简明教程,SB3,Stable Baseline](https://www.bilibili.com/video/BV1ty4y197JE?p=1)

### OpenAI Baselines (2017)

+ Github：[OpenAI Baselines](https://github.com/openai/baselines)

OpenAI Baselines是OpenAI于2017年发布的一套基于Python的高质量开源强化学习算法源码；这套源码涵盖了包括DQN、PPO在内的十种经典RL算法，是值得RL入门者学习的高质量代码

+ 机器学习框架：Tensorflow1（主分支）、Tensorflow2（分支`tf2`）
+ 演示：Gym（旧版的Gymnasium）、Mujoco（Mujoco 2.1.0）
+ 多进程：Multiprocessing

现已停止更新，由Stable Baselines继承后续开发