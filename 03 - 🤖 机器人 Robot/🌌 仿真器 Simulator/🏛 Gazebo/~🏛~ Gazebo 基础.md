+ 官网：[Gazebo](https://gazebosim.org/home)
+ FAQ：[[📑 FAQ - Gazebo]]
+ LTS：**Harmonic**，**Fortress**

Gazebo是运行于Ubuntu平台的开源仿真器，有着成熟的编程接口以及插件系统，与ROS系统联系紧密，在工业界使用较为广泛。

Gazebo存在两个开发分支

+ **Gazebo** - 原称“Gazebo Ignition”，是目前活跃的主分支，搭配ROS2使用，蓝色界面
+ **Gazebo Classic** - 原称“Gazebo”，已停止支持，版本以数字命名，灰色界面

**Harmonic**之后的版本，所有命名空间从`ign`改为`gz`

+ [[#安装配置]]
	+ [[#默认版本组合]]
		+ [[#Gazebo Fortress + ROS2 Humble]]
	+ [[#非默认版本组合]]
		+ [[#Gazebo Harmonic + ROS2 Humble]]
+ [[#世界建模]]
+ [[#命令行]]
	+ [[#Harmonic]]
	+ [[#Fortress]]

+ [[#ROS接口]]


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
## 世界建模

Gazebo的仿真模型（世界）使用基于`.xml`文件格式的`.sdf`文件描述，文件内需要定义的内容包括世界的物理特性、光照渲染、天气模拟等参数



---
## 命令行

Gazebo使用命令行系统调用相关的功能，命令的名称与格式在不同版本之间存在差异，可以使用选项`--help`查看命令的输入格式

+ **Harmonic** - `gz sim`
+ **Fortress** - `ign gazebo`

### Harmonic

+ `gz`
	+ `sim` - 
	+ `topic`
	+ `service`
### Fortress

+ `ign`
	+ `gazebo` - 启动仿真器
		+ `-v` (`--verbose`) - 设置调试文本输出级别（`-v 4`）
	+ `sdf` - 世界描述文件管理
	+ `topic` - 管理**话题**
		+ `-l` (`--list`) - 话题列表（注意：不会列出无发布者的节点）
		+ `-t` (`--topic`) - 此参数用于指定话题（`--topic /model/my_model/odometry`）
		+ `-i` (`--info`) - 查看指定话题的消息类型及发布者
		+ `-m` (`--`)
		+ `-p`( )

	+ `service` - 
	+ 

---
## ROS接口

+ 教程：[ROS整合](https://gazebosim.org/docs/fortress/ros2_integration/)、[README](https://github.com/gazebosim/ros_gz/blob/ros2/ros_gz_bridge/README.md)

ROS桥接模块可以将Gazebo的话题、服务、参数同步转接成为ROS的话题、服务、参数，与ROS的其他节点进行信息交换。桥接可以是单向或双向的

+ `<topic>` - Gazebo原消息名称
+ `<ros_msg_type>` - 对应的ROS消息类型，在此查阅：[README](https://github.com/gazebosim/ros_gz/blob/ros2/ros_gz_bridge/README.md)
+ `<gazebo_msg_type>` - Gazebo原消息类型，使用此命令查阅：`gz topic -t <topic> -m`

```bash
ros2 run ros_gz_bridge parameter_bridge <topic>@<ros_msg_type>@<gazebo_msg_type>
```

第二个`@`表示双向桥接，也可以设置为单向

+ `@` - 双向
+ `[` - 仅 ROS --> Gazebo
+ `]` - 仅 Gazebo --> ROS


---
## 插件

