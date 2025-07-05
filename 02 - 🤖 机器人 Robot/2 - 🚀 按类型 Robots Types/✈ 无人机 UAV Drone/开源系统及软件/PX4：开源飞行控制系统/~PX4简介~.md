+ Github：[PX4-Autopilot](https://github.com/PX4/PX4-Autopilot)
+ PX4 文档：[PX4 Guide](https://docs.px4.io/main/en/)

PX4全称PX4 Autopilot，是苏黎世瑞士联邦理工大学计算机视觉与几何实验室开发的开源飞行控制系统，在民用无人机领域与APM（Ardupilot）两足鼎立。

---
## 项目源码

PX4的项目源代码托管在Github上，包含依赖项在内的整个项目大小约为9GB，编译运行系统为Ubuntu Linux，可以使用`make`编译出以下内容：

+ PX4飞控固件：运行于飞行控制器模块FCU上，是无人机的核心控制算法
+ 仿真环境：基于Gazebo仿真器的硬件在环（HITL）及软件在环（SITL）仿真环境
+ 其他测试程序

---
## 文档导读