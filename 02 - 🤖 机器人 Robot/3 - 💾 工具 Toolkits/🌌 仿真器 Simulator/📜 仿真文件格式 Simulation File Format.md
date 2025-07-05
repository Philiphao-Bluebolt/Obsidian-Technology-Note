仿真器运行物理仿真时，各种**物体**所在的空间称为**环境**，物体和环境具有虚拟的物理、外观、约束等属性，这些属性通常需要一个外部描述文件储存，常用的文件描述格式有URDF、SDF、MJCF等

在物理仿真器中，机器人定义为关节连接连杆（物体）构成的**复合物体**

多数仿真器同时支持几种不同的物体或环境描述格式，但文件中某些仿真器独占的标签在被其他仿真器读取时会忽略，比如PyBullet加载SDF文件时会忽略其中定义Gazebo环境的标签

+ **前置知识**
	+ [[#格式支持]] - 仿真器与文件格式的支持关系
	+ [[#XML]] - URDF、SDF、MJCF文件使用的标记语言
+ **格式介绍**
	+ [[#URDF]] - ROS系统使用的格式，Gazebo支持，MuJoCo、PyBullet、IssacSim部分支持
	+ [[#SDF]] - Gazebo使用的格式，PyBullet、IssacSim部分支持
	+ [[#MJCF]] - MuJoCo使用的格式，PyBullet、IssacSim部分支持
	+ [[#USD]] - IssacSim使用的格式

---
## 格式支持

下面是仿真工具与描述文件格式的对应表

| 仿真器名称                             | URDF | SDF | MJCF | USD |
| --------------------------------- | ---- | --- | ---- | --- |
| 🏛 [[~🏛~ Gazebo 基础\|Gazebo]]     | ✔    | ✔   | ❌    | ❌   |
| 🥅 [[✨ MuJoCo 基本使用\|MuJoCo]]      | ✔    | ❌   | ✔    | ❌   |
| 🔫 [[~🔫~ PyBullet 基础\|PyBullet]] | ✔    | ✔   | ✔    | ❌   |
| ⚗ [IssacLab](⚗%20IsaacLab.md)     | ✔    | ✔   | ✔    | ✔   |
| 🌿 IssacGym                       |      |     |      |     |
| 🐞 Webots                         |      |     |      |     |


---
## XML

+ Wikipedia：[Extensible Markup Language](https://en.wikipedia.org/wiki/XML)

XML可扩展标记语言是一种用于数据储存的纯文本语言格式，数据以键值对的形式储存在XML文件中，通过分级标签排列成树状层级结构。XML语言是URDF、SDF、MJCF文件的格式基础。

XML文件由标签（Tag）、元素（Element）、属性（Attribute）组成，标签用于标识层级结构，内部可以包含子标签或元素形成树状层级结构，记录的数据以**元素**或**属性**的形式储存。

+ **标签**：以尖括号标识，有两种形式
	+ **起始及终止标签**：内夹带子元素，成对存在（`<book>`和`</book>`）
	+ **空标签**：不含子元素或子标签，以斜杠结束（`<price sgd="14.99"/>`）
+ **元素**：夹在标签之中的内容（`The Great Gatsby`）
+ **属性**：标签内的补充变量，可出现在起始标签或空标签内部（`category="fiction"`）

```xml
<?xml version="1.0" encoding="UTF-8"?>

<bookstore>
  <book category="fiction">
    <title lang="en">The Great Gatsby</title>
    <author>F. Scott Fitzgerald</author>
    <year>1925</year>
    <price sgd="14.99"/>
  </book>
  <book category="non-fiction">
    <title lang="en">Sapiens: A Brief History of Humankind</title>
    <author>Yuval Noah Harari</author>
    <year>2011</year>
    <price sgd="14.99"/>
  </book>
</bookstore>
```

---
## URDF

+ 文档：[URDF XML](https://wiki.ros.org/urdf/XML)
+ 仿真器支持：ROS、Gazebo、MuJoCo、IssacSim、Pybullet

URDF是ROS系统和Gazebo仿真器使用的机器人描述文件格式，文件后缀为`.urdf`，根标签为`<robot>`。一个URDF文件只能描述一个机器人。

URDF的连杆之前只能连接成树状结构，不能定义成环状结构

```xml
<?xml version="1.0" encoding="utf-8"?>


```




---
## SDF

+ 文档：[SDFormat](http://sdformat.org/spec)

SDF是由OSRF维护，Gazebo使用的默认文件类型，同一个SDF文件可以同时定义仿真环境的物理参数和多个模型



---
## MJCF 

+ MJCF文档：[XML Reference](https://mujoco.readthedocs.io/en/stable/XMLreference.html)
+ 建模教程：[Modeling](https://mujoco.readthedocs.io/en/latest/modeling.html)

MuJoCo的环境与物体在同一个XML文件中定义，文件所使用的定义语法称为**MJCF建模语言**。与所有XML文件一样，MJCF描述的模型文件有一个顶级标签，定义为`<mujoco>`；MJCF格式的文件名使用`.xml`作为后缀。


---
## USD

+ Wikipedia：[Universal Scene Discription](https://en.wikipedia.org/wiki/Universal_Scene_Description)

USD文件是由皮克斯开发的3D模型文件格式，常用的3D图形引擎和仿真器如Blender，Unreal均支持此格式，USD也是IssacSim仿真器（基于Nvidia Omniverse）的默认文件格式