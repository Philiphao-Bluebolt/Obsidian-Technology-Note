+ **文档**：[Python Documentation](https://docs.python.org/3/index.html)
+ **教程**：[官方](https://docs.python.org/3/tutorial/index.html)、[W3schools](https://www.w3schools.com/python/)、[Geeksforgeeks](https://www.geeksforgeeks.org/python-programming-language-tutorial/)、[菜鸟](https://www.runoob.com/python/python-tutorial.html)
+ **IDE**：[[~☄~ VSCode 使用教程#Python|VSCode]]、PyCharm、Spyder

Python是一门**解释型**高级编程语言，因其语法简单、扩展库丰富而受到广大开发者的欢迎，在数据分析、机器学习、应用开发等领域较为流行

+ [[#变量 Variable]]
	+ [[#布尔型 Boolean]]
	+ [[#数值 Value]]
	+ [[#字符串 String]]
	+ [[#序列 Sequence]]
	+ [[#字典 Dictionary]]
	+ [[#集合 Set]]
	+ [[#类型转换 Type Conversion]]
+ [[#逻辑 Logics]]
	+ [[#条件 Condition]]
	+ [[#循环 Loop]]
	+ [[#异常处理 Exception Handling]]
+ [[#函数 Function]]
	+ [[#自定义函数 Custom Functions]]
	+ [[#原生函数 Built-in Functions]]
+ [[#类与对象 Class & Object]]
+ [[#命令行调试 Command Line Debug]]
	+ [[#文本输出 Text Output]]
	+ [[#表格 Table]]
	+ [[#进度条 Progress bar]]
+ [[#库和模块 Library & Package]]
	+ [[#标准库 Standard Packages]]
	+ [[#第三方库 Third-Party Packages]]
		+ [[#专用库 Specialized Packages]]
		+ [[#小型库 Small Packages]]
	+ [[#自定义模块 Custom Modules]]
+ [[#安装及配置 Installation and Configuration]]

---
## 变量 Variable

+ **参考**：[Doc](https://docs.python.org/3/library/stdtypes.html)、[W3schools](https://www.w3schools.com/python/python_datatypes.asp)

Python中的变量相比其他常用的高级编程语言（如C++、Java）有以下特点：

1. 免声明：在定义时无需声明类型
2. 类型可变：在运行时可以通过赋值随意改变类型（不推荐）
3. 顶层设计：变量本质上都是类，设计更面向应用而非底层存储

Python常用变量类型如下：

| 类型        | 中文  | 类别  | 范例                    |
| --------- | --- | --- | --------------------- |
| `bool`    | 布尔型 | 真值  | `isNew = True`        |
| `int`     | 整型  | 数值  | `cnt = 11`            |
| `float`   | 浮点型 | 数值  | `val = -0.2`          |
| `complex` | 复数  | 数值  | `quat = `             |
| `str`     | 字符串 | 字符  | `name = "Alice"`      |
| `list`    | 列表  | 序列  | `index = [1, ab, 4]`  |
| `tuple`   | 元组  | 序列  | `tuple = (a, 4, 0.2)` |
| `range`   | 数列  | 序列  |                       |
| `dict`    | 字典  | 映射  |                       |
| `set`     | 集合  | 集合  |                       |

### 布尔型 Boolean

+ **参考**：[Doc](https://docs.python.org/3/library/stdtypes.html#boolean-type-bool)、[W3schools](https://www.w3schools.com/python/python_booleans.asp)

布尔型变量储存二元真值：`True`、`False`，布尔型变量之间可以进行与`and`、或`or`、非`not`运算操作，并使用`is`、`==`进行等值判断

布尔型变量可以参与数值运算，此时`True`自动转换为1，`False`自动转换为0

```python
isSafe = True
unlocked = False
isReady = isSafe and unlocked

if isReady is True:
	takeoff()
```

### 数值型 Value

+ **参考**：[Doc](https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex)、[W3schools](https://www.w3schools.com/python/python_numbers.asp)

Python的数值型变量有三种：整型`int`、浮点型`float`、复数`complex`

```python
x = 4
y = -1.5
c1 = 1 - 7j
c2 = complex(x, y)
```

+ **数值运算**
	+ **所有数值型**
		+ 二元运算
			+ 加减乘除：`+`、`-`、`*`、`/`
			+ 指数：`**`、`pow(x, y)`
		+ 一元运算
			+ 绝对值：`abs(x)`
			+ 共轭：`x.conjugate()`
	+ **仅整型**
		+ 求商、余数：`//`、`%`、`divmod(x, y)`
		+ 比特运算
			+ 按位与：`&`
			+ 按位或：`|`
			+ 按位取反：`~x`
			+ 按位异或：`^`
			+ 移位：`x<<n`、`x>>n`

### 字符串 String

+ **参考**：[Doc](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)、[W3schools](https://www.w3schools.com/python/python_strings.asp)

Python没有单独的字符类型，所有字符变量都以字符串类型保存。作为一种字符序列，其操作与列表、元组等类型相似

```python

```


### 序列 Sequence

+ **参考**：

Python有三种序列型变量，列表`list`、元组`tuple`、数列`range`，其中数列一般用在[[#循环 Loop|循环语句]]，很少单独使用，元组适合存放相对固定的数据，数列适合存放经常需要改动的数据

```python
# 元组 Tuple
my_tuple = ("red", "green", "blue", "a", "b", "c")

# 列表 List
my_list = []
 
```



### 字典 Dictionary


### 集合 Set



### 类型转换 Type Conversion

类型转换常发生在运算过程或数据处理过程中

#### 自动转换 Auto-Conversion

+ 



#### 强制转换 Forced-Conversion 



---
## 逻辑 Logics


### 条件 Condition

+ **关键词**：`if`、`elif`、`else`、`break`

```python
isPos = True
a = 1 if isPos else 0
```


### 循环 Loop

+ **关键词**：`for`、`in`、`while`、`break`、`continue`
+ **可迭代类型**：`str`、`list`、`tuple`、`dict`、`set`


Python支持两种循环语句：遍历型（`for ... in`）、当型（`while`），

遍历型循环（`for ... in`）的循环变量遍历一个**可迭代对象**的元素

```
```


满足条件时持续迭代


### 异常处理 Exception Handling

+ **关键词**：`try`、`except`、`else`、`finally`


---
## 函数 Function


### 原生函数 Built-in Functions

+ **参考**：[Doc](https://docs.python.org/3/library/functions.html)

Python原生函数一般用于变量类型转换



### 自定义函数 Custom Functions

+ **关键词**：`def`、`return`

Python使用`def`关键词定义函数，定义函数体的代码应在程序入口之前。函数可以有多个输出

```python
def add_and_subtract(a, b):
	x = a + b
	y = a - b
	return x, y
```

函数的传参输入可以指定默认值





### Lambda 表达式

+ **参考**：[Doc](https://docs.python.org/3/tutorial/controlflow.html#lambda-expressions)、


### 内函数 

内函数是在一个函数内部定义的函数





### 装饰器 Decorator






---
## 类与对象 Class & Object







---
## 命令行调试 Command Line Debug


### 文本输出 Text Output 

+ **函数**：`print()`

Python最常用的命令行文本打印函数是`print()`



[[ANSI 转义序列]]

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
## 库和模块 Package & Module

Python的库


将实现一定功能的函数或类封装成可调用的

Python的库（Package）内部封装着

Python官方及社区共同维护一系列功能强大的库

### 标准库 Standard Packages

标准库是由Python官方维护的扩展库，默认受Python解释器支持，不需要另外安装，直接使用`import`导入即可使用

| 库名称及文档    | 适用于       |     |
| --------- | --------- | --- |
| 🖥 os     |           |     |
| 🗂 shutil | 文件操作（偏顶层） |     |
| ⏰ time    | 时间计算      |     |
| 📟 math   | 调用数学函数    |     |
| 🎰 random | 伪随机数生成    |     |
| 🐢 turtle | 平面绘图      |     |

### 第三方库 Third-Party Packages

+ **库查询**：[Pypi / pip](https://pypi.org/)、[Anaconda / conda](https://anaconda.org/anaconda/repo?page=1)

第三方库指的是Python官方标准库以外的其他库，这些库通常以类和函数的形式提供封装好的算法和解决方案，涵盖各领域的通用算法以及软件工具的接口API，由各学术组织、基金会、公司维护

第三方库需使用`pip`或`conda`安装在当前Python环境后才能`import`

#### 专用库 Specialized Packages

| 库名称及文档                                                                       | 主模块名称（简称）           | 应用场景        | 学习笔记                             |
| ---------------------------------------------------------------------------- | ------------------- | ----------- | -------------------------------- |
| 🗃 [Numpy](https://numpy.org/doc/stable/user/index.html#user)                | `numpy` (`np`)      | 数组运算、数据处理   |                                  |
| 📈 [Matplotlib](https://matplotlib.org/stable/index.html)                    | `matplotlib`        | 数据绘图        | [[📈 Matplotlib\|Matplotlib]]    |
| 📊 [Pandas](https://pandas.pydata.org/docs/user_guide/index.html#user-guide) | `pandas` (`pd`)     | 数据分析        |                                  |
| 🎰 [Scipy](https://docs.scipy.org/doc/scipy/reference/index.html#scipy-api)  | `scipy`             | 科学计算优化      |                                  |
| 🖼 [OpenCV](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)        | `cv2`               | 计算机视觉、图像处理  | [[OpenCV Python 基本教程\| OpenCV]]  |
| 🌱 [Scikit-learn](https://scikit-learn.org/stable/)                          | `sklearn`           | 传统机器学习算法    |                                  |
| 🔦 [PyTorch](https://pytorch.org/docs/stable/index.html)                     | `torch`             | 机器学习库（偏科研）  | [[~🔦~ PyTorch 基本教程\| PyTorch]]  |
| ♨ [TensorFlow](https://www.tensorflow.org/api_docs/python/tf/all_symbols)    | `tensorflow` (`tf`) | 机器学习库（偏工业）  |                                  |
| 🍁 [Keras](https://keras.io/api/)                                            | `keras`             | 神经网络        |                                  |
| ⛳ [Gymnasium](https://gymnasium.farama.org/)                                 | `gymnasium` (`gym`) | 强化学习环境测试框架  | [[~⛳~ Gymnasium 基础\| Gymnasium]] |
| [🦁 PettingZoo](https://pettingzoo.farama.org/index.html)                    | `pettingzoo`        | 强化学习多智能体环境  |                                  |
| 🏀 [Stable Baselines](https://stable-baselines3.readthedocs.io/en/master/)   | `stable_baselines3` | 强化学习算法封装    |                                  |
| 🔫 [PyBullet](https://pybullet.org/wordpress/index.php/forum-2/)             | `pybullet` (`p`)    | 3D物理仿真器     |                                  |
| 🎛 [Control](https://python-control.readthedocs.io/en/0.10.1/#)              | `control`(`ct`)     | 控制器设计、仿真、分析 | [[🐍 Python - Control\|Control]] |
| 🚢 [Simple PID](https://simple-pid.readthedocs.io/en/latest/user_guide.html) | `simple_pid`        | 简单PID控制器实现  |                                  |
| 🧊 [CVXPY](https://www.cvxpy.org/)                                           | `cvxpy`(`cp`)       | 凸优化         |                                  |
|                                                                              |                     |             |                                  |

#### 小型库 Small Packages

| 库名称及文档                                                                  | 主模块名称         | 应用场景    | 学习笔记 |
| ----------------------------------------------------------------------- | ------------- | ------- | ---- |
| 📝 [PrettyTable](https://ptable.readthedocs.io/en/latest/tutorial.html) | `prettytable` | 命令行表格打印 |      |
| 🚥 [Tqdm](https://tqdm.github.io/)                                      | `tqdm`        | 进度条     |      |



### 自定义库 Custom Packages



### 模块导入 Import Modules




---
## 安装及配置 Installation and Configuration


### 虚拟环境 Virtual Environment



