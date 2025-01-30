+ 官方文档 - [Humble](https://docs.ros.org/en/humble)
+ 其他教程 - [古月居ROS2](https://www.bilibili.com/video/BV16B4y1Q7jQ/)、

ROS2是ROS的后继版本，为了让ROS系统适应工业界的要求，ROS2改进了ROS在分布式通讯功能方面的缺陷，更换了编译工具和编程API。

![[Pasted image 20250122132839.png]]

ROS2与ROS主要不同：

1. 通讯架构：`XML-RPC` --> `DDS`，不再有Master
2. 命令格式：统一为`ros2`
3. 编程接口：`roscpp` 、`rospy` --> `rclcpp`、`rclpy`
4. 编译工具：`catkin` --> `colcon`

+ [[#安装配置]]
	+ [[#版本选择]]
	+ [[#安装步骤]]
+ [[#基本概念]]
	+ [[#节点（Nodes）]]
	+ [[#话题（Topics）]]
	+ [[#服务（Services）]]
	+ [[#参数（Parameters）]]
	+ [[#动作（Action）]]
+ [[#编程开发]]
	+ [[#工作空间（Workspaces）]]
		+ [[#创建工作空间]]
	+ [[#功能包（Packages）]]
		+ [[#创建功能包]]
		+ [[#编写Python节点]]
		+ [[#编写C++节点]]
	+ [[#ROS2文件结构]]
+ [[#配套工具]]
	+ 

---
## 安装配置

+ 发行版列表 - [Distributions](https://docs.ros.org/en/humble/Releases.html)

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
sudo apt install ros-humble-ros-base
sudo apt install ros-dev-tools

# 配置环境变量
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```


---
## 基本概念

基于ROS2的机器人系统是一个由很多节点组成的图（Graph），节点之间通过消息与服务建立通讯，传递传感器数据、控制命令等数据流。

ROS2的基本概念与ROS相似，只是节点的注册与连接不再需要启动Master，只要系统中配置好ROS2，节点之间随时可以互相建立通讯连接。

![[Pasted image 20250122160431.png]]

### 节点（Nodes）

节点是ROS2系统的运行单元，使用C++或Python API编程实现。节点内部可以运行其他算法，节点之间的通信则通过话题和服务实现。ROS2自带的`rqt_graph`工具可用于查看当前系统的节点图。

```bash
rqt_graph
```

![[Screenshot from 2025-01-23 14-12-33.png]]

举个例子，一个基于视觉的无人机避障控制系统如果用ROS实现，可能会有下面几个节点。要注意节点的任务划分并不是唯一的

+ **传感器**节点通常由厂家提供，将传感器的测量数据从串口或局域网以ROS消息的格式输出
+ **点云处理**节点将传感器检测到的图像转换为3D点云
+ **建图**节点将点云数据转换为障碍物地图
+ **路径规划**节点计算无人机的避障轨迹
+ **导航**节点计算无人机需要执行的动作
+ **控制命令**节点将控制动作转换为Mavlink格式的命令传输给飞控

### 话题（Topics）




### 服务（Services）


### 参数（Parameters）


### 动作（Action）


---
## 编程开发

与ROS相比，ROS2对编译工具和编程接口进行了较大改变，编译工具`catkin`被`colcon`替代，C++与Python的接口`roscpp`和`rospy`也分别被`rclcpp`和`rclpy`替代

### 工作空间（Workspaces）

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

2. 初始化：生成`build`、`install`等目录

```bash
cd ~/xxx_ws
colcon test
```

### 功能包（Packages）

功能包是ROS2系统中封装好的库，功能包的目录包含节点源码、启动脚本、自定义的消息和服务类型。

+ ROS2安装的功能包：存放在ROS2的源文件路径
+ 用户自己创建的功能包：存放在某一工作空间的`src`文件夹中





#### 创建功能包







#### 编写Python节点




#### 编写C++节点







### ROS2源文件






---
## 配套工具


### Bag - 消息录制


### TF - 坐标变换


### Rqt - 多功能图形化面板


### Rviz - 数据3D可视化


### Gazebo - 仿真器


### PlotJuggler - 数据绘图分析



---
## 实际案例 - Turtlesim

