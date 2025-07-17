+ **链接**：[官网](https://www.anaconda.com/download/success)、[文档](https://docs.conda.io/en/latest/)

**Anaconda**是一个Python虚拟环境工具，提供了虚拟环境管理和库下载功能，其轻量版本为Miniconda。使用虚拟环境是为了解决电脑使用单个Python运行环境引起的库版本冲突问题，每一个虚拟环境提供一个独立的Python运行环境，不同虚拟环境之间的库相互隔离，互不干扰。

Anaconda使用命令行操作，其API命令为**Conda**，除了配置虚拟环境以外，Conda亦支持从Anaconda官方的数据库下载一些常用的第三方库，不过库列表没有Pip全

+ ⚙ [安装软件](#安装软件) - [下载](#下载) | [换源](#换源) | [更换文件路径](#更换文件路径) | [与ROS共存](#与ROS共存)
+ 🎨 [虚拟环境](#虚拟环境) - [创建](#创建) | [列表](#列表) | [删除](#删除) | [安装Python库](#安装Python库)
+ 🛠 [修改配置](#修改配置) - 
+ 🖥 [常用命令](#常用命令) - 

---
## 安装软件

### 下载

1. 从官网（[Anaconda](https://www.anaconda.com/download/success)）下载对应操作系统和硬件架构的版本安装器
	+ **Windows** - `.exe`
	+ **Linux** - `.sh`
2. 安装器运行
	+ **Windows** - 直接点击运行安装程序
	+ **Linux** - 使用`bash`命令运行自动安装脚本，中间显示的长篇条款可以按Esc快速跳过，最后一步添加环境变量要选同意，默认安装在执行命令的文件夹目录
3. 成功标志
	+ Windows：成功运行 Anaconda Prompt
	+ Linux：命令行的用户名前出现虚拟空间名称（默认`base`）

![[Screenshot from 2024-04-16 10-35-53.png]]

> ⭕ 如果之前通过`pip install conda`安装了Conda，一定要用`pip uninstall conda `卸载掉原有的Conda以后再安装Anaconda。

> ⭕ Windows系统下Anaconda默认**不**修改环境变量以防止旧项目的Python环境被覆盖，此时无法在Windows命令行使用Conda命令，只能使用Anaconda Prompt


### 换源

Conda命令安装第三方库时默认使用位于国外的官网下载源，下载速度很慢，因此需要换成国内的镜像下载源，如果电脑本身就位于国外的话则不一定需要更换。

将[Tuna教程](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)提供的文本复制到`.condarc`文件里

```.condarc
channels:
  - defaults
show_channel_urls: true
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
```

### 更换文件路径

默认情况下，Anaconda会把虚拟环境和库文件存放在Windows系统的C盘，大量的库文件会显著压缩C盘的容量，这时就需要更换这个路径。直接修改Anaconda的设置`.condarc`文件即可

```
pkgs_dirs:
  - E:/conda
  - D:/conda/pkgs

envs_dirs:
  - E:/

```

> ⭕ 经试验，由于未知问题，不能直接使用创建符号链接的方法移动虚拟环境和库文件，否则Anaconda的默认虚拟环境会出错。

### 与ROS共存

如果需要同时用到ROS和Anaconda，应该先安装ROS，再安装Anaconda

如果ROS使用的Python版本和虚拟环境的Python版本不匹配，可能会导致rospy节点无法初始化，因此在新建虚拟环境之前，应该先查看ROS使用的Python环境

```bash
# 退出所有虚拟环境
conda deactivate

# 启动Python时会显示版本号
python3
```

新建虚拟环境时将Python版本指定为与ROS的Python版本一致






---
## 虚拟环境



### 创建

创建新的名为`my_env`的虚拟环境（指定Python版本）

```bash
conda create --name my_env python=3.8.0
```

> ⭕ 使用命令创建新的虚拟环境时，如果在结尾没有写Python，则虚拟环境不包含Python解释器，也不能使用Pip，这时可以用`conda install python`补充下载

新创建的虚拟环境`my_env`需要激活

```bash
conda activate my_env
```

Linux系统下，可以设置虚拟环境`my_env`为默认，在打开新命令行时自动激活：打开`.bashrc`，将`conda activate my_env`加在Conda初始化的命令之后

Windows系统下，可以在Anaconda Prompt的属性页面里修改起始虚拟环境与起始目录：目标一栏改为默认起始虚拟环境的文件夹，起始位置则改为默认开启目录

![[Pasted image 20240425101204.png]]

### 列表

当前激活的虚拟环境会显示一个星号

```bash
conda env list
```

### 删除

注意不能直接删除当前激活的虚拟环境，要先退出才能删

```bash
conda deactivate
conda remove --name my_env --all
```


### 安装Python库

Conda的库比Pip的要少很多，推荐用Pip下载：[🧊 Pip](🧊%20Pip.md)

安装Numpy

```bash
conda install numpy
```


---
## 修改配置

Anaconda的配置文件

需要修改的`.condarc`文件使用下面的命令生成。

```bash
conda config --set show_channel_urls yes
```







---
## 常用命令

> **虚拟环境**

```

```


> **配置**