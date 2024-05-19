+ 官网：[Anaconda](https://www.anaconda.com/)
+ Conda文档：[Conda](https://docs.conda.io/en/latest/)

Anaconda是一个Python库管理工具，它可以创建相互独立的Python虚拟环境，不同版本的库可以独立运行于不同的虚拟环境中，防止版本冲突

Anaconda提供的命令行库下载工具为Conda，Conda的兼容性版本检测比Pip更严格，但提供的包比Pip少，缺少的包只能通过Pip下载

[[#安装（Ubuntu）]]
[[#更换镜像源]]
[[#创建虚拟环境]]

---
## 安装（Ubuntu）

+ 参考：[超详细Ubuntu安装Anaconda步骤+Anconda常用命令](https://blog.csdn.net/KRISNAT/article/details/124041869?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171323235516800178553371%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171323235516800178553371&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-124041869-null-null.142^v100^pc_search_result_base2&utm_term=ubuntu%20anaconda&spm=1018.2226.3001.4187)

在官网选择Linux版本，有x86和ARM64架构两种选择，选择合适的架构下载`.sh`安装文件
![[Pasted image 20240416101421.png]]

用命令行`bash`运行安装文件，一直按住Enter跳过冗长的条款，输入“yes”，Anaconda默认会安装在执行命令的文件夹目录。

这里有个小问题，如果原本通过`pip install conda`安装了`conda`，一定要用`pip uninstall conda `卸载掉以后再安装Anaconda。

成功的标志是命令行的前面有显示当前激活的虚拟空间`base`

![[Screenshot from 2024-04-16 10-35-53.png]]

---
## 更换镜像源

+ 清华Tuna教程：[Anaconda 镜像使用帮助](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)

默认的下载源在国外，下载速度很慢，因此需要换成国内的下载源，需要修改的`.condarc`文件使用下面的命令生成

```bash
conda  config  --set  show_channel_urls  yes
```

将Tuna教程提供的文本复制到`.condarc`文件里

---
## 创建虚拟环境

创建新的名为`my_env`的虚拟环境（指定Python版本）

```bash
conda  create  --name  my_env  python=3.8.0
```

激活虚拟环境`my_env`

```bash
conda  activate  my_env
```

将虚拟环境`my_env`设置为默认（打开命令行时自动激活）

+ Linux：修改`.bashrc`

```bash
# 加在Conda初始化的命令之后
conda  activate  my_env
```

+ Windows：修改Anaconda Prompt属性页面，起始位置——默认开启目录，目标——默认起始虚拟环境的文件夹

![[Pasted image 20240425101204.png]]


---
## 查看虚拟环境列表

当前激活的虚拟环境会显示一个星号

```bash
conda  env  list
```

---
## 安装Python库

Conda的库比Pip的要少很多，推荐用Pip下载：[[Pypi - Pip：包下载及管理工具]]

安装Numpy

```bash
conda  install  numpy
```

---
## 删除虚拟环境

注意不能直接删除当前激活的虚拟环境，要先退出才能删

```bash
conda  deactivate
conda  remove  --name  my_env  --all
```

---
## 与ROS共存

如果需要同时用到ROS和Anaconda，应该先安装ROS，再安装Anaconda

如果ROS使用的Python版本和虚拟环境的Python版本不匹配，可能会导致rospy节点无法初始化，因此在新建虚拟环境之前，应该先查看ROS使用的Python环境

```bash
# 退出所有虚拟环境
conda  deactivate

# 启动Python时会显示版本号
python3
```

新建虚拟环境时将Python版本指定为与ROS的Python版本一致



