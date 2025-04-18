这篇文章对机器人学的学科研究目标和知识体系做高度总结，略去复杂的数学公式推导。

机器人学理论的经典研究内容是**串联刚体工业机器人**的运动控制与规划问题，这些基础理论可用于指导更复杂的机器人系统（如无人机、腿式机器人）的设计。


+ **机器人基础 Robot Basis**
	+ [[#工业机器人基本结构 Basic Structure of Industrial Robots]]
		+ [[#关节 Joint]]
		+ [[#末端执行器 End Effector]]
	+ [[#坐标变换 Coordinate Transform]]
+ **运动学 Kinematics**
	+ [[#机器人工作空间 Robot Working Cell]]
	+ [[#前向运动学 Forward Kinematics]]
	+ [[#逆向运动学 Inverse Kinematics]]
+ 动力学 - 力学控制

---
## 工业机器人基本结构 Basic Structure of Industrial Robots

+ **控制目标**：末端执行器（工件）的位姿
+ **设计参考**：人类手臂
+ **重要部件**：关节、末端执行器（工件）

典型的串联工业机器人仿照人类手臂的结构设计，部件按照“基座-关节-连杆-关节-...-末端执行器”的顺序安装，是运动学模型最简单的机器人。

![[Pasted image 20240911151348.png]]

三维空间中有六个自由度，分别是沿三个方向的平移运动和绕三个方向的旋转运动。机器人对末端执行器的位姿控制本质上是对自由度的控制，一个由电机驱动的关节便控制一个自由度。

![[Pasted image 20240925165008.png]]
### 关节 Joint

+ **按运动类型**：旋转 vs 平移
+ **按控制的自由度**：主轴 vs 副轴

与人类的球关节不同，机器人的每个关节只可执行一个方向的**旋转**或者**平移**运动，控制末端执行器的一个自由度，称为轴（Axis）。

关节的数量和类型是工业机器人的一个分类标准，也决定机器人可以控制的自由度数量。机器人必须至少有六个轴才可能完全控制六个自由度，多于六个轴的**冗余设计**则会带来更大的灵活性。

![[Pasted image 20240927160233.png]]
根据控制的工件自由度类型，关节分为控制平移自由度的主轴（Major Axes）和控制旋转自由度的副轴（Minor Axes），一般工业机器人的主轴都在副轴之前（靠近基座）。

人类抓握物体时，腰关节（Waist）、肩关节（Shoulder）、肘关节（Elbow）为主轴，控制手的平移运动，因此我们有时候也把六自由度机器人的前三个主轴称为腰、肩、肘。


### 末端执行器 End Effector

末端执行器或工件通常是夹爪、焊枪，


---
## 坐标变换 Coordinate Transform

+ **理论目标**：找到工件位姿的表示方法，本质上是找到点在不同坐标系的坐标转换方法
+ **数学基础**：线性代数与空间解析几何

坐标变换理论解决的问题是

1. 如何描述一个坐标系相对于另一个坐标系的位置；
2. 如何对同一个点在两个不同坐标系下的坐标进行转换；

### 主动与被动变换 Active and Passive Transform






---
## 机器人工作空间 Robot Working Cell

机器人的工作空间是其所有可能的工件位型的集合


---
## 前向运动学 Forward Kinematics

+ **已知**：关节参数$q_1,q_2,q_3,...,q_n$
+ **待求**：末端执行器位型$T_{base}^{tool}$（用坐标变换矩阵表示）

前向运动学的任务是建立

### DH参数法


### 指数积法



---
## 逆向运动学 Inverse Kinematics