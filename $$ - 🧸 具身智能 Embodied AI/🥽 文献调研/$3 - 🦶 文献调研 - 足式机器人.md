足式机器人是目前（2025）学术界和工业界最热门的机器人类型之一。这篇文章的目的是简要概括足式机器人相关技术的发展状况、技术前沿以及难点。

+ **简介**

+ **感知**（[总论](#足式机器人%20-%20感知)）

+ **导航**（[总论](#足式机器人%20-%20导航)）

+ **运控**（[总论](#足式机器人%20-%20运动控制)）

---
## 足式机器人 - 简介

+ 为什么要有
+ 怎么动起来
+ 


足式机器人按照形态可分为以下类型

+ **按腿数**：单足、双足、四足、六足……
+ **按腿形态**：
+ **按足尖**：点足式、平足式、轮足式

足式机器人三大任务

---
## 足式机器人 - 感知








内状态 ZMP、CoM

Proprioceptive vs Exteroception

---
## 足式机器人 - 导航


---
## 足式机器人 - 运动控制

+ 难点？
+ 现有方法？（强化学习、MPC）
+ 





---
## 论文阅读

> **[Perception for Humanoid Robots](https://arxiv.org/pdf/2309.15616)** （2023）

文章介绍了近年来人形机器人的主要感知技术、遇到的挑战以及解决方案，也提到主流的人形机器人感知算法的设计思路逐渐从基于确定性算法转向基于**多传感器融合与AI技术**。

作者把文章涉及的感知技术分为三类：**内部状态估计**（Internal State Estimation）、**外部环境理解**（External Environment Understanding）、**人机交互**（HBI, Human Robot Interaction），其中人机交互有时被视为特殊的外部环境检测任务。

内部状态估计对机器人的，


> **[Sim-to-Real: Learning Agile Locomotion For Quadruped Robots](https://arxiv.org/pdf/1804.10332)**（2018）

这篇文章是最早将强化学习应用于四足机器人运动控制的论文之一，不仅在仿真环境中完成了训练，还在四足机器人实机上做了实验。文章讨论了控制模型从仿真环境移植到实机遇到的问题以及解决方案。

Bayesian optimization
Central Pattern Generator controller
CACLA-inspired algorithm
phase-parametric policies

> 



---
## 参考

+ 知乎
	+ [RL做足式机器人运控的经典必读文章](https://zhuanlan.zhihu.com/p/29806809248)
+ 论文
	1. [A Comprehensive Review on Autonomous Navigation](https://arxiv.org/pdf/2212.12808)
	2. [Perception for Humanoid Robots](https://arxiv.org/pdf/2309.15616)