+ 官网：[https://gazebosim.org/home](https://gazebosim.org/home)

Gazebo是运行于Ubuntu平台的开源仿真器，有着成熟的编程接口以及插件系统，与ROS系统联系紧密，在工业界使用较为广泛。

Gazebo曾经存在两个开发分支，目前活跃的分支原称“**Gazebo Ignition**”，界面为蓝色调；旧版则称为“Gazebo Classic”，界面为灰色调，版本以数字命名

+ [[#安装配置]]
	+ [[#默认版本组合 Gazebo Fortress + ROS2 Humble]]
	+ [[#非默认版本组合 Gazebo Harmonic + ROS2 Humble]]
+ [[#世界建模]]
+ [[#命令行]]
+ [[#ROS系统联动]]


---
## 安装配置

选择Gazebo的发行版本需要考虑两个因素，Ubuntu平台的版本和ROS的版本，每一个ROS2版本都默认对应一个Gazebo版本，若不使用官方推荐的ROS2-Gazebo对应版本则需要另外安装桥接接口。


### 默认版本组合 Gazebo Fortress + ROS2 Humble

Gazebo Fortress是ROS2 Humble的官方默认搭配，直接使用下列命令安装即可（假定已经提前安装好ROS2）

```bash
sudo apt install ros-humble-ros-gz
```

### 非默认版本组合 Gazebo Harmonic + ROS2 Humble

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
```

---
## 世界建模

Gazebo的仿真模型（世界）使用基于`.xml`文件格式的`.sdf`文件描述，文件内需要定义的内容包括世界的物理特性、光照渲染、天气模拟等参数



---
## 命令行

Gazebo使用命令行系统调用相关的功能



---
## ROS系统联动