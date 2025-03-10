+ 官网：[PyBullet](https://pybullet.org/wordpress/)
+ 范例：[Github-Pybullet](https://github.com/bulletphysics/bullet3/tree/master/examples/pybullet)
+ FAQ：[[📑 FAQ - PyBullet]]

Bullet是C++编写的轻量级仿真器，PyBullet是Bullet的Python接口，安装时需要C++编译环境。

+ **基础**
	+ [[#客户端与服务端]]
	+ [[#仿真模型]]
+ **模型导入**
	+ [[#URDF导入]]
+ **运动控制**
	+ [[#关节控制]]


+ [[#其他工具]]
	+ [[#运动学工具]]
	+ [[#调试工具]]
+ [[#官方教程]]

---
## 客户端与服务端

Pybullet仿真器基于服务端-客户端模型

+ **客户端** - 用户编写的Python API程序，负责从服务端接受数据，处理数据以及发送控制命令
+ **服务端** - 物理仿真器，负责物理、渲染运算

```python
physicsClient = p.connect(p.GUI)
```

一个客户端可以同时连接多个服务端，此时发送命令时需要指定服务端的ID


---
## 仿真模型

仿真模型即为PyBullet中的物体，物体由连杆、关节组成，物体之间可以构建约束。

+ **物体**（Body）：分为单个刚体和多体
	+ **多体**（Multibody）：由多个连杆通过关节连接而成，机器人模型即属于多体
		+ **连杆**（Link）：由几何体或网格文件描述的单个刚体
			+ **碰撞体**（Collision Shape）：用于物理仿真的碰撞接触相关运算
			+ **可视体**（Visual Shape）：用于渲染物体的外形
		+ **关节**（Joint）：连接两个连杆并构建运动学约束，每个关节都自带一个执行器
+ **约束**（Constraint）：与关节类似，但可以在仿真运行时修改，没有转动约束

上述的每一个实体类型都由一个独特的非负整数ID标识，唯一例外是多体的连杆使用编号-1标识基座。

物体可以通过导入外部文件或使用函数直接创建，由于机器人模型涉及的参数众多，一般先使用CAD软件（SolidWork、Creo等）建模，再导入其[[~📜~ 仿真器及文件格式 Simulator and File Format|模型描述文件]]

---
## 导入URDF




---
## 


---
## 关节控制



---
## 运动学工具


---
## 其他工具

Pybullet提供了机器人运动学以及输入输出相关的函数工具支持运动学计算和仿真调试







### 调试工具

调试工具包括绘制直线、文本，设置按钮、滚动条，获取键盘、鼠标输入



---
## 官方教程

这份教程是Bullet作者亲自编写的文档

![[pybullet_quickstartguide.pdf]]


