## 版本选择

ROS的发行版本与Ubuntu的版本一一对应，与Ubuntu系统一样，每两年发布一个长期支持版（Long-term Support），安装时，ROS的版本一定要与Ubuntu系统的版本对应。

由于目前（2024年）正处于ROS与ROS2的过渡时期，运行于Ubuntu 20.04的Noetic已是第一代ROS系统的最终发行版，Ubuntu 22.04以及未来的系统将搭配ROS2，不再支持ROS。不过目前ROS2的社区和软件支持还未成熟，大多数的开发者还在使用第一代ROS。

+ 目前开发常用的ROS版本如下：
1)        Ubuntu 18.04 – ROS [Melodic](https://wiki.ros.org/melodic/Installation/Ubuntu)
2)        Ubuntu 20.04 – ROS [Noetic](https://wiki.ros.org/noetic/Installation/Ubuntu)
3)        Ubuntu 22.04 – ROS2 [Humble](https://docs.ros.org/en/humble/Installation.html)

---
## 下载安装

ROS与ROS2的下载步骤有一定区别，具体参考对应版本下载页面上的教程。下面是基本通用的安装步骤说明：添加下载源 >> curl下载密钥 >> 更新apt源 >> apt下载 >> 配置环境变量

以一代ROS的最终发行版ROS Noetic安装为例，依次在命令行输入：

```bash
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

$ sudo apt install curl

$ curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add

$ sudo apt update

$ sudo apt install ros-noetic-desktop-full

$ echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
```

如果用curl命令获取密钥的速度很慢，可以直接在当前路径创建一个名为“ros.asc”的文件，浏览器打开上面curl提到的网页，把文本复制到新创建的文件里，运行“sudo apt-key add ros.asc”

---
## 主文件访问

安装成功后，ROS的主文件夹位于以下路径：

```bash
cd /opt/ros/<distros>  #<distros>代表当前下载的发行版
```

![[Pasted image 20240309151157.png]]

---
## 卸载

有时候ROS出现一些难以排查的问题，我们希望卸载重装整个ROS系统，卸载的命令如下：

```bash
sudo  apt  remove  ros-*
sudo  apt  autoremove

#第一行自动卸载所有ROS相关的软件包；第二行卸载所有额外的依赖项
```

