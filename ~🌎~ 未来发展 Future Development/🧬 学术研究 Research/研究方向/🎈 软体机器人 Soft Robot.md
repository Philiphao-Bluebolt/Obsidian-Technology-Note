+ Wikipedia：[Soft robotics](https://en.wikipedia.org/wiki/Soft_robotics)

软体机器人是机器人的一个分支，研究由柔性材料所构成的机器人的设计、建造、控制方面的问题。这个方向比较新，目前没有很成熟的技术，但很有研究前景

软体机器人是材料、机械、电路、控制的交叉学科。

---
## 基本介绍

### 优缺点（与刚体机器人相比）

+ 优势：
	+ 对人安全：由于其结构柔软，碰撞到人体时造成的伤害较小，可以设计成贴身的机器人
	+ 不易因撞击损坏：柔软材料不易因撞击损坏
	+ 空间利用率高：机器人可以弯曲折叠甚至压缩，便于储存、搬运
	+ 延展性：可以深入一些较难进入的空洞
+ 劣势：
	+ 建模困难：已有的多自由度刚体机器人模型不能使用
	+ 传感器选择局限：无法使用光电编码器、IMU等传统刚体机器人传感器
	+ 材料的局限性：发展依赖新型材料的发现
	+ 力输出过小：软体机器人刚度不足，难以输出较大的力
	+ 精度问题：柔软的材料更容易受外力扰动影响，且运动规律复杂，难以精确控制移动

软体机器人的设计需要考虑其**材料性质、驱动机制、控制方法**，而且这几个要素往往是紧密相关的

### 驱动机制 Actuation Mechanics

+ **流体驱动（Fluidic-driven）**- 利用流体（气体）产生的压力驱使柔软结构运动
	+ 挤压式夹爪（Jamming-based Gripper）- 无需实时反馈
	+ 分段式设计（Origami Structure）- 提高刚度和负载上限
	+ 气动（Pneumatic）
		+ 气动人工肌肉（Pneumatic Artificial Muscles, PAM）- 利用气室气压产生牵引力和推力
+ **电驱动（Electric-driven）**- 
	+ 直接驱动（Direct）- 静电场直接对材料产生作用力，能量转换效率高，设备简单
		+ 介电弹性体执行器（DEA）- 利用电极化产生的正负电荷作用力使材料变形
		+ 压电材料（Piezoelectric Material）- 
		+ 离子电激活聚合物执行器（IEAPA）-
		+ 水凝胶（Hydrogel）- 
		+ 电流变体材料（Electrorheological fluid, ER Fluid）- 混有导电微粒的绝缘材料，刚度随电场强度变化而改变
		+ 静电吸附装置（Electroadhesive Devices, EA）- 利用电场将需要夹持的物体电极化从而产生吸引力
	+ 间接驱动（Indirect）- 电能转换成其他形式的能量（热、光），再对材料产生作用力
		+ 形状记忆合金（SMA）- 低温时柔软可塑，加热后恢复原来的形状
		+ 液晶弹性体（LCE）- 热相变导致的可逆形变可以产生极大的力
		+ 扭曲聚合物（Twisted and Coiled Polymer, TCP）-  加热时分子扭曲产生纵向拉力
		+ 光曲执行器（Light-mediated Bending Actuators）- 受光时产生弯曲
+ **磁驱动（Magnetic-driven）**
	+ 直接驱动（Direct）- 磁场对材料产生力的作用
		+ 磁流变液（Magnetorheological Fluid, MR Fluid）- 刚度和粘度随磁场强度变化
	+ 间接驱动（Indirect）- 磁场转化为其他形式的能量对材料产生作用力
		+ 磁形状记忆合金（MSMA）- 高刚度，但输出力小且难以塑性
		+ 无线供能（Wireless Power Transfer WPT）

### 建模方法 Modeling Method

+ （Piecewise Constant Curvature, PCC）


### 控制策略 Control Strategy

+ 低阶控制（Low-level Control）

+ 开环控制（Open-loop）

---
## 研究现状




---
## 应用前景

+ 医疗机器人：

+ 洞穴勘探、救灾：

+ 家居护理：

+ 可动玩具：

---
## 参考资料

+ 团体组织
	+ [IEEE International Conference on Soft Robotics](https://www.ieee-ras.org/conferences-workshops/fully-sponsored/robosoft) - IEEE 软体机器人大会
	+ [Soft Robotics Lab Sungkyunkwan University](https://www.youtube.com/@softroboticslab4460) - 韩国成均馆大学软体机器人实验室
+ 项目
	+ 流体驱动
		+ [NASA-funded BYU inflatable robots](https://www.youtube.com/watch?v=pjx9m5mONrE) - NASA资助美国杨百翰大学充气机器人项目
		+ [Inflatable Ant-Roach Robot](https://spectrum.ieee.org/inflatable-antroach-robot-is-big-enough-to-ride) - Otherlab研发的仿蚂蚁充气机器人
		+ [Electrohydraulic Gripper](https://www.youtube.com/watch?v=wWL5oMK_CRk) - 德国MPI-IS研发的电动液压软夹爪
	+ 磁驱动
		+ [Magnetic soft robots using fiber-based processes](https://www.youtube.com/watch?v=dQtXeYN57wk) - MIT磁驱纤维微型机器人
+ 论文
	+ Design, fabrication and control of soft robots - Daniela Rus, Michael T. Tolley
	+ [Toward perceptive soft robots: Progress and challenges](https://onlinelibrary.wiley.com/doi/full/10.1002/advs.201800541) - 