+ 官网：[PyBullet](https://pybullet.org/wordpress/)
+ 范例：[Github-Pybullet](https://github.com/bulletphysics/bullet3/tree/master/examples/pybullet)

Bullet是C++编写的轻量级仿真器，PyBullet是Bullet的Python接口，安装时需要C++编译环境。

+ [[#基本概念]]
	+ [[#客户端与服务端]]
	+ [[#物体]]
	+ [[#连杆]]
	+ [[#关节]]
+ [[#创建物体]]
	+ [[#URDF导入]]
+ [[#其他工具]]
+ [[#官方教程]]

---
## 基本概念

### 客户端与服务端

Pybullet仿真器基于服务端-客户端模型，一个客户端可以同时连接多个服务端

+ **客户端** - 用户编写的Python API程序，负责从服务端接受数据，处理数据以及发送控制命令
+ **服务端** - 物理仿真器，负责物理、渲染运算

```python
physicsClient = p.connect(p.GUI)
```

### 物体

物体（Body）是


### 连杆


### 关节




---
## 创建物体




### URDF导入



---
## 控制



---
## 其他工具

Pybullet提供了机器人运动学相关的函数




### 输入



---
## 官方教程

这份教程是Bullet作者亲自编写的文档

![[pybullet_quickstartguide.pdf]]


