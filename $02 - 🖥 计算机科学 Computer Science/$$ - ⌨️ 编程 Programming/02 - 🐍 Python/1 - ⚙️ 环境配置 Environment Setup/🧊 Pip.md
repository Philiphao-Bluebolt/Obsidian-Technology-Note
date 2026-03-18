+ **链接**：[官网](https://pypi.org/)、[文档](https://pip.pypa.io/en/stable/)

**Pip**是Python官方第三方库仓库**Pypi**（Python Package Index）所提供的配套下载工具，所有Python运行环境都自带Pip，无需手动下载

+ 🖥 [常用命令](#常用命令)

---
## 常用命令

> **安装库**

```bash
# 默认下载最新版
pip install numpy

# 指定版本下载
pip install numpy==2.3.0

# 指定源下载
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple 

# 根据依赖项列表下载
pip install -r ./requirements.txt 

```

> **管理库**

```bash
# 查看库所有可用版本，也可以在官网上查
pip index versions numpy

# 查看库详细信息
pip show numpy

# 更新编译工具
pip install --upgrade setuptools wheel
```


> **配置**

```bash
# 查看Pip软件版本及位置
pip --version

# 查看配置文件地址及选项值
pip config -v list
```


---
## 更换下载源

1. 定位Pip配置文件的位置：`pip config -v list`
