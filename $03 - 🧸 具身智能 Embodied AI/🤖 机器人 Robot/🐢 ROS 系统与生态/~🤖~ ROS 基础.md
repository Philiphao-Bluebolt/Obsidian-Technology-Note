+ 文档 - [Humble](https://docs.ros.org/en/humble)
+ 教程 - [官方](https://docs.ros.org/en/humble/Tutorials.html)、[古月居ROS2](https://www.bilibili.com/video/BV16B4y1Q7jQ/)
+ 编程 - [[💾 ROS 编程开发]]

ROS2是ROS的后继版本，为了让ROS系统适应工业界的要求，ROS2改进了ROS在分布式通讯功能方面的缺陷，更换了编译工具和编程API。

![[Pasted image 20250122132839.png]]

ROS2与ROS主要不同：

1. 通讯架构：`XML-RPC` --> `DDS`，不再有Master
2. 命令格式：统一为`ros2`
3. 编程接口：`roscpp` 、`rospy` --> `rclcpp`、`rclpy`
4. 编译工具：`catkin` --> `colcon`

+ 📦 [[#安装配置]]：[[#版本选择]] | [[#安装步骤]]
+ 💎 [[#核心概念]]：[[#节点 Node|节点]] | [[#话题 Topic|话题]] | [[#服务 Service|服务]] | [[#参数 Parameter|参数]] | [[#动作 Action|动作]] | [[#接口 Interface|接口]]（[[#消息 Message|消息]] | [[#服务类型 Service|服务类型]] | [[#动作类型 Action|动作类型]]）
+ 💾 [[#命令行]]
	+ [[#主系统命令 ros2]]：[[#run]] | [[#launch]] | [[#pkg]] | [[#node]] | [[#topic]] | [[#service]] | [[#action]] | [[#param]] | [[#interface]] | [[#bag]] | [[#daemon]] | [[#component]] | [[#doctor]]
	+ [[#编译命令 colcon]]：[[#build]] | [[#clean]] | [[#list]] | [[#test]]
+ 🧩 [[#编程开发]]
	+ 路径：[[#工作空间 Workspace|工作空间]] | [[#功能包]]（[[#创建C++功能包|C++]] | [[#创建Python功能包|Python]] | [[#创建双语言功能包|双语言]]）| [[#ROS源文件 Source Files|ROS源文件]] 
	+ 内容：[[#实现节点|节点]]（[[#创建C++节点|C++]] | [[#创建Python节点|Python]]）| [[#定义接口|接口]]（[[#定义消息|消息]] | [[#定义服务类型|服务类型]] | [[#定义动作类型|动作类型]]）| [启动脚本](#启动脚本)（[[#使用Python格式|Python]] | [[#使用XML格式|XML]]）
+ 🛠 [[#配套工具]] - [[#Bag]] | [[#TF]] | [[#Rqt]] | [[#Rviz]] | [[#Gazebo]] | [[#PlotJuggler]] | [[#MoveIt]] | Control | Turtlebot
+ 🏆 [[#实际案例]] - [[#Turtlesim]]

---
## 安装配置

+ 发行版列表：[Distributions](https://docs.ros.org/en/humble/Releases.html)

ROS2与Ubuntu类似，每两年发布一个LTS长期支持版（维护5年），每一个ROS版本都与一个Ubuntu发行版一一对应

### 版本选择

由于ROS2每个版本之间的基础功能基本相同且不提倡跨版本使用，选用版本时主要考虑项目需要用到的库和接口的兼容性。

最新版本虽然支持时间最长，但社区教程较少，传感器、仿真器等外设软硬件的接口也没有立刻跟进，因此一般选用**最新版本的上一个长期稳定版**

+ [Jazzy](https://docs.ros.org/en/jazzy/Installation.html)（Ubuntu 24.04）- 最新
+ [Humble](https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debs.html)（Ubuntu 22.04）- 最常用

### 安装步骤

ROS2通过Ubuntu命令行安装，所有版本的安装步骤都可以归结为下面三部：设置ROS下载源 --> apt下载 --> 配置环境变量

+ **ROS2 Humble 安装命令**

```bash
# 加载Ubuntu全局软件包
sudo apt install software-properties-common
sudo add-apt-repository universe

# 添加ROS2下载源
sudo apt update && sudo apt install curl -y

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

# 更新下载源
sudo apt update
sudo apt upgrade

# 安装ROS2
sudo apt install ros-humble-desktop

sudo apt install ros-dev-tools

# 配置环境变量

```

---
## 核心概念

基于ROS2的机器人系统是一个由若干节点组成的图（Graph），节点之间通过消息与服务建立通讯，传递传感器数据、控制命令等数据流。

ROS2的基本概念与ROS相似，只是节点的注册与连接不再需要启动Master，只要系统中配置好ROS2，节点之间随时可以互相建立通讯连接。

![[Pasted image 20250122160431.png]]

### 节点 Node

+ **命令**：`ros2 node`

节点（Node）是ROS2系统的运行单元，使用ROS2提供的C++或Python API编程实现。节点内部可以运行其他算法，节点之间的通信则通过话题和服务实现。ROS2自带的`rqt_graph`工具可用于查看当前系统的节点图。

```bash
rqt_graph
```

![[Screenshot from 2025-01-23 14-12-33.png]]

#### 节点实例

如果用ROS实现一个基于视觉的无人机避障控制系统，系统内部可能会有下面几个节点。

+ **传感器**节点通常由厂家提供，将传感器的测量数据从串口或局域网以ROS消息的格式输出
+ **点云处理**节点将传感器检测到的图像转换为3D点云
+ **建图**节点将点云数据转换为障碍物地图
+ **路径规划**节点计算无人机的避障轨迹
+ **导航**节点计算无人机需要执行的动作
+ **控制命令**节点将控制动作转换为Mavlink格式的命令传输给飞控

节点的任务划分一般根据编程与数据传输的要求来确定，并不是唯一的

### 话题 Topic

+ **命令**：`ros2 topic`

话题（Topic）是节点之间的异步通讯方式，其运行原理基于发布-订阅模型（Publish-subscribe Pattern），通讯模型类似现实中的无线电。节点可以发布消息到指定的话题，也可以从指定的话题读取消息。

实现话题的发布（Publish）和接收（Subscribe）有三种方式：

+ 节点编程、命令行、Rqt工具组件

消息（Message）是话题使用的数据传输格式，属于接口（Interface）的一种，发布数据到指定话题时必须使用对应的消息格式。

#### 话题实例

假设无人机的IMU（惯性测量模块）测量到无人机的六轴速度（线速度、角速度），要将这个速度以话题的形式发布到ROS系统。

速度话题发布应选用消息`geometry_msgs/msg/TwistStamped`，这条消息描述了一个带时间戳的六轴速度数据格式

```msg
# A twist with reference coordinate frame and timestamp

std_msgs/Header header
	builtin_interfaces/Time stamp
		int32 sec
		uint32 nanosec
	string frame_id
Twist twist
	Vector3  linear
		float64 x
		float64 y
		float64 z
	Vector3  angular
		float64 x
		float64 y
		float64 z

```

### 服务 Service

+ **命令**：`ros2 service`

服务（Service）以一应一答的方式构建节点之间的同步通讯，类似现实中的对讲机。节点可以其他节点的服务函数



### 参数 Parameter

+ **命令**：`ros2 param`

参数（Parameter）是由用户定义，可以被所有节点自由访问的ROS变量。参数可以使用命令修改，以文本形式储存或从文本中读取



### 动作 Action

+ **命令**：`ros2 action`



### 接口 Interface

+ **命令**：`ros2 interface`

接口（Interface）是消息、服务类型、动作类型的统称，接口以文本形式定义了话题、服务、动作的数据传输格式

#### 消息 Message


#### 服务类型 Service


#### 动作类型 Action



---
## 命令行

ROS2使用命令行接口进行操作，主系统命令名称为`ros2`，编译工具命令名称为`colcon`。输入命令时如果忘记了格式，可以使用`--help`查看参数输入格式以及含义

### 主系统命令 ros2

+ `ros2`
	+ [[#run]] - 运行指定功能包的**单个节点**（`ros2 run my_package my_node`）
	+ [[#launch]] - 运行指定功能包的**启动文件**（`ros2 launch my_package my_launch`）
	+ [[#pkg]] - 管理功能包
	+ [[#node]] - 管理**节点**
		+ `list` - 查看所有活跃节点 
		+ `info` - 查看指定节点信息
	+ [[#topic]] - 管理**话题**
		+ ``
	+ [[#service]] - 管理**服务**
	+ [[#action]] - 管理**动作**
	+ [[#param]] - 管理**参数**
	+ [[#interface]] - 管理
	+ [[#bag]]
	+ [[#daemon]]
	+ [[#component]]
	+ [[#doctor]] - 系统自检

### run


### launch


### pkg


### node


### topic


### service


### action


### param


### interface


### bag


### daemon


### component


### doctor


### 编译命令 colcon

+ `colcon`


### build 



### clean


### list 


### test



---
## 编程开发

+ **详见**：[[💾 ROS 编程开发]]

与ROS相比，ROS2对编译工具和编程接口进行了较大改变，编译工具`catkin`被`colcon`替代，C++与Python的接口`roscpp`和`rospy`也分别被`rclcpp`和`rclpy`替代


### 工作空间 Workspace

工作空间由用户自己创建，是存放、编译自定义功能包的目录，其路径一般位于Home文件夹中，完成初始化的工作空间文件结构如下

+ 📁 `xxx_ws`
	+ 📁 `build` - 编译生成的可执行文件
	+ 📁 `install` - 
	+ 📁 `log` - 日志
	+ 📁 `src`- **存放功能包**

#### 创建工作空间

1. 新建工作空间文件夹，按惯例命令为`xxx_ws`

```bash
mkdir -p ~/xxx_ws/src
```

2. 初始化：生成`build`、`install`等目录，配置环境变量

```bash
cd ~/xxx_ws
colcon test
echo "source ~/xxx_ws/install/setup.bash" >> ~/.bashrc
```

### 功能包 Package

+ **命令**：`ros2 pkg`

功能包是ROS2系统中封装好的库，功能包的目录包含节点源码、启动脚本、自定义的消息和服务类型。

+ ROS2安装的功能包：存放在ROS2的源文件路径
+ 用户自己创建的功能包：存放在某一工作空间的`src`文件夹中

与一代ROS不同，ROS2创建功能包时需要指定包内使用的编程语言。若想创建同时支持Python和C++的功能包则需要额外配置。

ROS2创建功能包的命令是`ros2 pkg create`

#### 创建C++功能包

```bash
cd ~/xxx_ws/src
ros2 pkg create --build-type ament_cmake my_cpp_package
```

C++功能包的默认文件结构如下

+ 📁 `my_cpp_package`
	+ 📁 `include` - 存放依赖项文件
		+ 📁 `my_cpp_package`
	+ 📁 `src` - **存放C++源码文件**
	+ 📄 `CMakeLists.txt` - **编译配置**
	+ 📄 `package.xml` - 软件包基本信息

#### 创建Python功能包

```bash
cd ~/xxx_ws/src
ros2 pkg create --build-type ament_python my_py_package
```

Python功能包的默认文件结构如下

+ 📁 `my_py_package`
	+ 📁 `resource`
		+ 📄 `my_py_package`
	+ 📁 `test`
		+ 📜 `test_copyright.py`
		+ 📜 `test_flake8.py
		+ 📜 `test_pep267.py
	+ 📁 `my_py_package` - **存放Python源码文件**
	+ 📄 `package.xml` - 软件包基本信息
	+ 📄 `setup.cfg` - 
	+ 📜 `setup.py` - 

#### 创建双语言功能包

```bash

```



### 实现节点

节点本质上是使用C++或Python编写的程序

#### 创建C++节点

+ **参见**：



#### 创建Python节点



### 定义接口


#### 定义消息


#### 定义服务类型


#### 定义动作类型



### 启动脚本

启动脚本可以同时打开多个节点，设置参数等功能

#### 使用Python格式


#### 使用XML格式




### ROS源文件 Source Files

ROS2系统的源文件存放在这个文件夹：`/opt/ros/<distro>`，其中`<distro>`是ROS2版本名称。




---
## 配套工具

ROS系统内部提供的工具

### Bag


### TF


### Rqt


### Rviz


### Gazebo

+ **参见**：[官网](https://gazebosim.org/home)、[🏛 Gazebo 基础](~🏛~%20Gazebo%20笔记导览.md)

Gazebo是ROS系统配套的机器人仿真器，使用SDF文件定义环境，支持导入以URDF文件形式定义的机器人。

每个ROS发行版都搭配了一个推荐的Gazebo版本，可以使用下列命令下载：

```bash
sudo apt install ros-<distro>-ros-gz
```


### PlotJuggler

+ **参见**：

### MoveIt


---
## 实际案例

### Turtlesim

