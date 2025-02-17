+ 文档：[Python Documentation](https://docs.python.org/3/index.html)
+ 教程：[官方](https://docs.python.org/3/tutorial/index.html)、[W3schools](https://www.w3schools.com/python/)、[Geeksforgeeks](https://www.geeksforgeeks.org/python-programming-language-tutorial/)

Python是一种解释型高级语言，因其语法简单、扩展库丰富而受到广大开发者的欢迎，在数据分析、机器学习、应用开发等领域较为流行

+ [[#变量 Variable]]
	+ [[#基本变量 Basic Variables]]
	+ [[#线性容器 Linear Container]]
	+ [[#字符串 String]]
	+ [[#运算 Operation]]
+ [[#语法 Syntax]]
	+ [[#条件 Condition]]
	+ [[#循环 Loop]]
	+ [[#异常处理 Exception Handling]]
+ [[#函数 Function]]
+ [[#类与对象 Class & Object]]
+ [[#命令行调试 Command Line Debug]]
	+ [[#文本打印 Print Text]]
	+ [[#表格 Table]]
	+ [[#进度条 Progress bar]]
+ [[#库和模块 Library & Package]]
	+ [[#标准库 Standard Libraries]]
	+ [[#第三方库 Third-Party Libraries]]
	+ [[#自定义模块 Custom Modules]]
+ 

---
## 变量 Variable

### 基本变量 Basic Variables


### 线性容器 Linear Container

Python原版有四种常用的线性数据容器

```python
# 元组 Tuple
my_tuple = ("red", "green", "blue", "a", "b", "c")

# 列表 List
my_list = []

# 集合 Set
my_set = 

# 字典 Dictionary
my_dict = 
```

| 容器            | 可重复 | 有顺序 |     |     |
| ------------- | --- | --- | --- | --- |
| 元组 Tuple      |     |     |     |     |
| 列表 List       |     |     |     |     |
| 集合 Set        |     |     |     |     |
| 字典 Dictionary |     |     |     |     |

### 字符串 String






### 运算 Operation









---
## 语法 Syntax


### 条件 Condition

+ **关键词**：`if`、`elif`、`else`

Python的



### 循环 Loop

+  **关键词**：``


### 异常处理 Exception Handling

+ **关键词**：`try`、`except`、`else`、`finally`


---
## 函数 Function

+ **关键词**：`def`、`return`

Python使用`def`关键词定义函数，不需要指定返回类型

```python
def adder(a, b):
	y = a + b
	return y
```

### 内函数 

内函数是在一个函数内部定义的函数


### 装饰器 Decorator

+ 参考：[一文看懂Python系列之装饰器(decorator)](https://blog.csdn.net/qq_44955314/article/details/127066758?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171333894116777224487292%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171333894116777224487292&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-127066758-null-null.142^v100^pc_search_result_base2&utm_term=python%20decorator&spm=1018.2226.3001.4187)



---
## 类与对象 Class & Object







---
## 命令行调试 Command Line Debug


### 文本打印 Print Text 

+ **函数**：`print()`

Python最常用的命令行文本打印函数是`print()`



+ 参见：[[ANSI 转义序列]]

Python的`print`

```python
print("\033[31mRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRRR\033[0m")
print("\033[33mYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYYY\033[0m")
print("\033[32mGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGG\033[0m")
print("\033[36mCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCCC\033[0m")
print("\033[34mBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB\033[0m")
print("\033[35mMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMMM\033[0m")
```

![[Pasted image 20240426134440.png]]

### 表格 Table

+ PrettyTable文档：[PTable](https://ptable.readthedocs.io/en/latest/tutorial.html)

PrettyTable库可以在命令行输出简约美观的表格，此外，它还支持从数据库、CSV文件读入数据制表。

```python
from  prettytable  import  PrettyTable

my_table = PrettyTable()
my_table.title = "Dragon List"
my_table.field_names = ["Name", "Clan", "Age"]

my_table.add_row(["Bluebolt", "Electro", 12])
my_table.add_row(["Flaminton", "Fire", 8])
my_table.add_row(["Stanley", "Electro", 8])
```

### 进度条 Progress bar



---
## 库和模块 Library & Package


### 标准库 Standard Libraries

标准库是由Python官方维护的扩展库，默认受Python解释器支持，不需要另外安装

| 库名称及文档    | 适用于  |     |
| --------- | ---- | --- |
| 🖥 os     |      |     |
| 🗂 shutil | 文件操作 |     |
| ⏰ time    |      |     |
| 📟 math   |      |     |
| 🎰 random |      |     |
|           |      |     |

### 第三方库 Third-Party Libraries

第三方库指的是Python官方标准库以外的其他库，需要使用`pip`安装。这些库通常以类和函数的形式提供封装好的算法和解决方案，涵盖各领域的通用算法以及软件工具的接口API，由学术组织、基金会、公司维护

下面的表格收录各领域常用的第三方库，不包括一些使用面较窄的库

| 库名称及文档                                                                       | 主模块名称               | 应用场景        | 学习笔记                            |
| ---------------------------------------------------------------------------- | ------------------- | ----------- | ------------------------------- |
| 🗃 [Numpy](https://numpy.org/doc/stable/user/index.html#user)                | `numpy` (`np`)      | 向量矩阵运算、数据处理 |                                 |
| 📈 [Matplotlib](https://matplotlib.org/stable/index.html)                    | `matplotlib`        | 数据绘图        |                                 |
| 📊 [Pandas](https://pandas.pydata.org/docs/user_guide/index.html#user-guide) | `pandas` (`pd`)     | 数据分析        |                                 |
| 🎰 [Scipy](https://docs.scipy.org/doc/scipy/reference/index.html#scipy-api)  | `scipy`             | 科学计算优化      |                                 |
| 🖼 [OpenCV](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)        | `cv2`               | 计算机视觉、图像处理  | [[OpenCV Python 基本教程\| OpenCV]] |
| 🔦 [PyTorch](https://pytorch.org/docs/stable/index.html)                     | `torch`             | 机器学习库（偏科研）  |                                 |
| ♨ [TensorFlow](https://www.tensorflow.org/api_docs/python/tf/all_symbols)    | `tensorflow` (`tf`) | 机器学习库（偏工业）  |                                 |
| ⛳ [Gymnasium](https://gymnasium.farama.org/)                                 | `gymnasium`         | 强化学习环境测试及搭建 |                                 |
| 🏀 [Stable Baselines](https://stable-baselines3.readthedocs.io/en/master/)   | `stable_baselines3` | 强化学习算法框架    |                                 |
| 🎛 [Control](https://python-control.readthedocs.io/en/0.10.1/#)              | `control`           | 控制器设计、仿真、分析 |                                 |
| 🚢 [Simple PID](https://simple-pid.readthedocs.io/en/latest/user_guide.html) | `simple_pid`        | 简单PID控制器实现  |                                 |
| 🔫 [PyBullet](https://pybullet.org/wordpress/index.php/forum-2/)             | `pybullet` (`p`)    | 3D物理仿真器     |                                 |
|                                                                              |                     |             |                                 |

### 自定义模块 Custom Modules




### 



