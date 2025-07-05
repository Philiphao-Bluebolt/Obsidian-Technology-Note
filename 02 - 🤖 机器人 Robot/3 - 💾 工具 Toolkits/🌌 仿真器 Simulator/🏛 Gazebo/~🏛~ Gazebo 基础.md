+ 官网：[Gazebo](https://gazebosim.org/home)
+ FAQ：[[📑 FAQ - Gazebo]]
+ 文件：[📜 SDF](📜%20SDF%20文件.md)、[📜 URDF](📜%20URDF%20文件.md)

Gazebo是运行于Ubuntu平台的开源仿真器，有着成熟的编程接口以及插件系统，与ROS系统联系紧密，在工业界使用较为广泛。Gazebo存在两个开发分支

+ **Gazebo** - 原称“Gazebo Ignition”，是目前活跃的主分支，搭配ROS2使用，蓝色界面
+ **Gazebo Classic** - 原称“Gazebo”，已停止支持，版本以数字命名，灰色界面

目前活跃的长期发行版为**Harmonic**、**Fortress**

+ ⚙ **安装配置**：[总览](#安装配置)
	+ 🏛 版本选择：[[#默认]] | [[#非默认]]
	+ ⚡ 测试：
+ 🏞 **环境与界面**：[环境](#环境建模%20Environment%20Modeling)（光源、重力、风）| 模型（摩擦）| [插件](#插件)
+ 🦾 **模型**：
+ 🔗 **仿真控制**：
	+ 🖥 原生命令：
	+ 🤖 ROS接口：[总览](#Gazebo%20ROS%20接口) | [话题](#话题桥接) | 

---
## 安装配置

选择Gazebo的发行版本需要考虑两个因素，Ubuntu平台的版本和ROS的版本，每一个ROS2版本都默认对应一个Gazebo版本，若不使用官方推荐的ROS2-Gazebo对应版本则需要另外安装桥接接口。

### 默认版本组合 

#### Gazebo Fortress + ROS2 Humble

Gazebo Fortress是ROS2 Humble的官方默认搭配，直接使用下列命令安装即可（假定已经提前安装好ROS2）

```bash
sudo apt install ros-humble-ros-gz

# 启动测试
ign gazebo 
# ign gazebo -v 4 --render-engine ogre
```

### 非默认版本组合 

#### Gazebo Harmonic + ROS2 Humble

Gazebo Harmonic并不是官方推荐的ROS2 Humble搭配版本，不能直接下载`ros`开头的Gazebo软件包，只能分别安装仿真器软件本体和桥接接口。

```bash
# 安装依赖项
sudo apt update
sudo apt install curl lsb-release gnupg

# 配置下载源
sudo curl https://packages.osrfoundation.org/gazebo.gpg --output /usr/share/keyrings/pkgs-osrf-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/pkgs-osrf-archive-keyring.gpg] http://packages.osrfoundation.org/gazebo/ubuntu-stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/gazebo-stable.list > /dev/null

sudo apt update

# 安装Gazebo本体
sudo apt install gz-harmonic

# 安装ROS-Gazebo话题桥接接口
sudo apt install ros-humble-ros-gzharmonic

# 启动测试
gz sim
```




---
## 环境 Environment 

Gazebo的仿真环境分为“世界”与

使用基于`.xml`文件格式的`.sdf`文件描述，文件内需要定义的内容包括世界的物理特性、光照渲染、天气模拟等参数

### 光源 Light


### 重力 Gravity


### 风 Wind


---
## 模型 Model 


### 导入






### 插件

+ 文档：[System Plugin](https://github.com/gazebosim/gz-sim/tree/gz-sim7/src/systems)（位于源码头文件的注释）

插件是Gazebo官方提供的功能扩展模块

| 插件源码                                                                                                                | 功能          |
| ------------------------------------------------------------------------------------------------------------------- | ----------- |
| [Ackermann Steering](https://github.com/gazebosim/gz-sim/tree/gz-sim7/src/systems/ackermann_steering)               | 提供阿克曼转向速度控制 |
| [Joint Controller](https://github.com/gazebosim/gz-sim/tree/gz-sim7/src/systems/joint_controller)                   | 关节速度/力矩控制器  |
| [Joint Position Controller](https://github.com/gazebosim/gz-sim/tree/gz-sim7/src/systems/joint_position_controller) | 关节位置控制器     |
| [Joint State Publisher](https://github.com/gazebosim/gz-sim/tree/gz-sim7/src/systems/joint_state_publisher)         | 关节状态发布      |
| [Odometry Publisher](https://github.com/gazebosim/gz-sim/tree/gz-sim7/src/systems/odometry_publisher)               | 里程计信息发布     |

Gazebo插件的储存位置：`/usr/lib/x86_64-linux-gnu`


---
## 原生命令

Gazebo使用命令行系统调用相关的功能，命令的名称与格式在不同版本之间存在差异，可以使用选项`--help`查看命令的输入格式（**Fortress** 版本的命名空间为`ign`而非`gz`）

+ `gz`：**（Fortress 版本为`ign`）**
	+ `sim`：启动仿真器 **（Fortress 版本为`gazebo`）**
		+ `-v` (`--verbose`)：设置调试文本输出级别（`-v 4`）
		+ `--render-engine`：指定渲染引擎（`--render-engine ogre`）
	+ `sdf`：仿真文件管理
	+ `topic`：管理**话题**
		+ `-t` (`--topic`)：指定话题（`-t /model/my_model/odometry`）
		+ `-l` (`--list`)：活跃话题列表，无发布者的话题除外
		+ `-i` (`--info`)：查看指定话题的消息类型及发布者
		+ `-m` (`--`)：
		+ `-p`( )：
	+ `service`：管理服务
		+ `-s` (`--service`)：指定服务（`-s /world/empty/create`）
		+ `-l` (`--list`)：活跃服务列表
		+ ``


---
## Gazebo ROS 接口

+ 安装：[ROS整合](https://gazebosim.org/docs/fortress/ros2_integration/)
+ 文档：[ROS Index](https://index.ros.org/?search_packages=true&pkgs=ros_gz)
+ 源码：[ros_gz](https://github.com/gazebosim/ros_gz/tree/ros2)

Gazebo提供了一系列ROS软件包以实现Gazebo-ROS的桥接，通过调用软件包的启动文件或节点可以直接从ROS控制Gazebo

+ `ros_gz_sim` - 仿真器启动、模型导入
+ `ros_gz_bridge` - 话题与服务桥接
+ `ros_gz_image` - 
+ `ros_gz_interfaces`
+ `ros_gz_point_cloud`

### 启动仿真与导入模型

使用`ros_gz_sim`可以支持从ROS端打开Gazebo或者导入URDF模型，效果与原生命令（`gazebo`或`ign`）相同

+ **启动仿真**（`gz_sim.launch.py`启动脚本）

```bash
# Run by ROS
ros2 launch ros_gz_sim gz_sim.launch.py gz_args:="empty.sdf -v 4"

# Run by Gazebo cmd ("ign gazebo" for Fortress)
gz sim empty.sdf -v 4
```

参数 `gz_args` 的字符串用于指定额外的仿真启动选项，格式与原生命令相同


+ **导入URDF模型**（`create`节点）

```bash
# Import by ROS
ros2 run ros_gz_sim create -file 'robot.urdf'

# Import by Gazebo cmd ("ign" for Fortress)
gz service -s "/world/<world_name>/create" -r ""
```

常用参数如下（支持使用`--help`查询）

+ `-file`：URDF文件地址及名称
+ `-name`：定义仿真器中模型名称
+ `-world`：指定模型导入到的世界名称

### 话题桥接

+ 教程：[README](https://github.com/gazebosim/ros_gz/blob/ros2/ros_gz_bridge/README.md)

使用`ros_gz_bridge`可以将Gazebo话题同步转接为ROS话题。桥接的数据传输可以是单向或双向的，用ROS命令发布消息时使用ROS消息的格式，用Gazebo命令发布时使用Gazebo的格式

+ **启动桥接节点**

```bash
ros2 run ros_gz_bridge parameter_bridge <topic>@<ros_msg_type>@<gazebo_msg_type>
```

+ `<topic>` - Gazebo原消息名称`
+ `<ros_msg_type>` - 对应的ROS消息类型，在此查阅：[README](https://github.com/gazebosim/ros_gz/blob/ros2/ros_gz_bridge/README.md)
+ `<gazebo_msg_type>` - Gazebo原消息类型，使用此命令查阅：`gz topic -t <topic> -m`

第一个`@`无特殊意义，第二个`@`用于指定桥接方向：

+ `@` - 双向桥接
+ `[` - 单向桥接（仅 Gazebo --> ROS）
+ `]` - 单向桥接（仅 ROS --> Gazebo）

同一个桥接节点可以桥接多对ROS-Gazebo话题，只需在输入参数时用空格隔开即可

### 服务桥接

+ 教程：[README](https://github.com/gazebosim/ros_gz/blob/ros2/ros_gz_bridge/README.md#example-4-service-bridge)

使用`ros_gz_bridge`也可以将Gazebo服务转接为ROS服务，此时不需要指定服务的数据类型。只能从ROS端调用Gazebo的服务

+ **启动桥接节点**

```bash
ros2 run ros_gz_bridge parameter_bridge <service>@<ros_>
```

