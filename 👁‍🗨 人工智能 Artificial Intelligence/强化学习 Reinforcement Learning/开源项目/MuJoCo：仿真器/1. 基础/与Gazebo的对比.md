+ Gazebo：[[~Gazebo简介~]]

MuJoCo和Gazebo都是机器人领域常用的仿真器，相比之下，MuJoCo经常被描述为更加轻便，而Gazebo更加臃肿

---
## 关节的描述

+ Gazebo SDF：刚体（连杆）`<link>`和关节`<joint>`是平级的标签，两者都是模型`<model>`的子标签，刚体之间的连接关系通过关节的父`<parent>`、子`<child>`标签描述

+ MuJoCo XML：刚体`<body>`之间的父子连接关系通过标签的级别描述，关节`<joint>`则是刚体的子标签，描述该刚体与其父刚体的关节约束

---
## 世界与模型

+ Gazebo SDF：世界和模型的SDF文件是分开的，先打开世界，再摆放模型；即使用ROS启动文件自动打开也是这个逻辑

+ MuJoCo XML：世界和模型在一个XML文件中定义，同时打开

---
## 外部接口

+ Gazebo ROS：Gazebo倾向于和ROS一起使用，使用Gazebo ROS的话题和服务作为接口

+ MuJoCo API：MuJoCo提供了C++和Python的API，其中考虑到和别的强化学习模块的结合，Python的API库`mujoco`比较常用

