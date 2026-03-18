+ [[#世界（World）]]
	+ 用户操作界面（GUI）
	+ 场景（Scene）
	+ 球坐标系（Spherical Coordinates）
	+ 物理（Physics）
	+ 环境（Atmosphere）
	+ 风（Wind）
	+ [[#模型（Model）]]
		+ 连杆（Link）
		+ 关节（Joint）
	+ 光源（Light）

+ 其他概念
	+ 实体（Entity）
	+ 属性（Property）
	+ 状态（State）

---
### 世界（World）

世界指的是Gazebo仿真中的完整环境，包含所有的模型、物理环境参数（如重力加速度、温度、气压），世界可以被保存为SDF文件

---
### 模型（Model）

模型是SDF文件定义的刚体或刚体组合体，由连杆和关节组成。

关于模型的创建方法参见建模部分

---
### 实体（Entity）

Gazebo中的实体是一个很泛化的概念，通常出现在服务请求中，模型、连杆、关节、光源甚至物理属性（如重力）都可以称之为实体


