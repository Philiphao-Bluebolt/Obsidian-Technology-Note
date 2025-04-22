+ **文档**：[Python Documentation](https://docs.python.org/3/index.html)、[PEP 8 代码风格](https://peps.python.org/pep-0008/)
+ **教程**：[官方](https://docs.python.org/3/tutorial/index.html)、[W3schools](https://www.w3schools.com/python/)、[Geeksforgeeks](https://www.geeksforgeeks.org/python-programming-language-tutorial/)、[菜鸟](https://www.runoob.com/python/python-tutorial.html)

Python是一门**解释型**面向对象脚本~~胶水~~高级编程语言，因其语法简单、扩展库丰富而受到广大开发者的欢迎，在数据分析、机器学习、应用开发等领域较为流行

+ ⚙ **开发环境配置**（[总览](#开发环境配置%20Environment%20Setup) | [解释器](#解释器%20Interpreter) | [IDE](#集成开发环境%20IDE)）
	+ 🧊 Pip - [PyPi](#Pip%20-%20PyPi) |
	+ 🐍 Conda - [安装](#安装) | 
+ 📐 **变量类型及运算**（[总览](#变量类型及运算%20Variables%20&%20Operations) | [赋值](#赋值%20Assignment) | [引用](#引用%20Reference) | [作用域](#作用域%20Scope) | [类型转换](#类型转换%20Type%20Conversion)）
	+ 🚙 单值 - [布尔型](#布尔型%20Boolean) | [数值型](#数值型%20Value)（[整型](#整型%20Integer) | [浮点型](#浮点型%20Float) | [复数](#复数%20Complex)）
	+ 🚝 序列 - [序列](#序列%20Sequence)（[列表](#列表%20List) | [元组](#元组%20Tuple) | [范围](#范围%20Range)）| [字符串](#字符串%20String) 
	+ 🛸 其他 - [字典](#字典%20Dictionary) | [集合](#集合%20Set)
+ 💬 **语法及逻辑**（[总览](#语法及逻辑%20Syntax%20&%20Logics)）
	+ 📜 语法 - [缩进](#缩进%20Indentation)
	+ ⚖ 判断 - [条件](#条件%20Condition) | [循环](#循环%20Loop) | [异常处理](#异常处理%20Exception%20Handling)
+ 💾 **输入及输出**（[总览](#输入及输出%20Input%20&%20Output)）
	+ 💻 命令行 - [文本](#文本输出%20Text%20Output) | [表格](#表格%20Table) | [进度条](#进度条%20Progress%20bar) | 命令传参
	+ 📁 文件 - 路径 | 纯文本 | 图片 | 其他
+ 📦 **代码封装**（[总览](#代码封装%20Encapsulation)）
	+ 📞 函数 - [自定义](#自定义函数%20Custom%20Functions) | [内函数](#内函数%20Nested%20Function) | [Lambda](#Lambda%20表达式) | 递归 | [原生函数](#原生函数%20Built-in%20Functions)
	+ 🕹 类 - 自定义（继承 | 实例化）| 成员（属性 | 方法）
	+ 🚀 方法 - [修饰器](#修饰器%20Decorator) | 抽象 | 私有 | 运算符重载
+ 🗃 **库与模块**（[总览](#库和模块%20Package%20&%20Module) | [导入](#模块导入%20Import%20Modules)）
	+ 🏁 类型 - [标准库](#标准库%20Standard%20Packages) | [第三方库](#第三方库%20Third-Party%20Packages)（[专用库](#专用库%20Specialized%20Packages) | [小型库](#小型库%20Small%20Packages)）
	+ ✂ 自定义 - [自定义](#自定义模块%20Custom%20Modul) | 

```python
if __name__ == "__main__":
	print("Hello World!")
```

---
## 开发环境配置 Environment Setup

Python程序通过解释器执行，解释器是

### 解释器 Interpreter



### 集成开发环境 IDE


### Pip - PyPi


#### 



### Conda

+ 官网下载：[Anaconda](https://www.anaconda.com/download/success)

Anaconda是一个Python虚拟环境管理工具，在不同的虚拟环境中安装不同版本的Python解释器以及第三方库，互不冲突。对应的命令行工具为`conda`，`conda`命令亦支持直接下载一些常用的第三方库。Anaconda的轻量版本为Miniconda

#### 安装

Windows和Linux的下载方式类似

1. 从官网（[Anaconda](https://www.anaconda.com/download/success)）下载对应操作系统的版本安装器（Windows为`.exe`，Linux为`.sh`）
2. 安装器运行
	+ Windows：点击运行
	+ Linux：使用`bash`命令运行，跳过长篇条款，最后一步添加环境变量要选同意
3. 成功标志
	+ Windows：成功运行 Anaconda Prompt
	+ Linux：命令行的用户名前出现虚拟空间名称（默认`base`）

#### 虚拟空间管理




---
## 变量类型及运算 Variables & Operations

+ **参考**：[Doc](https://docs.python.org/3/library/stdtypes.html)、[W3schools](https://www.w3schools.com/python/python_datatypes.asp)

Python中的变量相比其他常用的高级编程语言（如C++、Java）有以下特点：

1. 无需声明：在定义时无需声明类型
2. 类型可变：在运行时可以通过赋值随意改变类型（不推荐）
3. 顶层设计：变量本质上都是指向类的引用，设计更面向应用而非底层存储

常用变量类型如下：

| 类型        | 中文       | 类别   | 赋值范例                            |
| --------- | -------- | ---- | ------------------------------- |
| `bool`    | 布尔型      | 真值型  | `isNew = True`                  |
| `int`     | 整型       | 数值型  | `cnt = 11`                      |
| `float`   | 浮点型      | 数值型  | `val = -0.2`                    |
| `complex` | 复数       | 数值型  | `quat = `                       |
| `str`     | 字符串      | 字符序列 | `name = "Alice"`                |
| `list`    | 列表       | 序列型  | `index = [1, ab, 4]`            |
| `tuple`   | 元组       | 序列型  | `rcd = (a, 4, 0.2)`             |
| `range`   | 范围（等差数列） | 序列型  | `num_seq = range(1, 2, 20)`     |
| `dict`    | 字典       | 映射型  | `enc = {"love": 11, "you": -4}` |
| `set`     | 集合       | 集合型  | `group = {1, 2, 'all', 'I'}`    |

### 赋值 Assignment

+ **类型标注**

对变量赋值时可以使用顿号标注变量的类型，但这种方式并不能“锁定”变量类型；在变量类型遭到修改时依然不会报错。

```python
my_integer : int
my_str : tuple[str, str] = (1, 2)

my_integer = "str"
my_str = 1
```

+ **多变量赋值**

允许使用同一个赋值号对多个不同的变量进行赋值，变量之间使用逗号隔开。这种写法常用于获取函数的多个输出。

```python
cnt, text, value, isFine = 3, "Yes", 0.1, True
pos, vel = getOdometry()
```

+ **三目运算符**

这是一种二分条件赋值的简化写法

```python
my_value = -1 if isNeg else 1
```


### 引用 Reference

Python的变量本质上都是指向对象的引用，仅传递变量引用而没有创建新对象的复制方式为浅拷贝（Shallow Copy），与深拷贝相对应。直接指定变量名称拷贝时（`b = a`）总是默认浅拷贝。

+ **可变类型的浅拷贝**

可变类型（Immutable）如列表`list`的元素可以被直接修改，由于`ls_b`和`ls_a`指向同一列表对象，经由`ls_b`修改列表的元素值也会影响`ls_a`；可使用**范围切分**赋值`[:]`指定深拷贝

```python
ls_a = [1, 2]

ls_b = ls_a # Shallow copy
ls_b[0] = 2
print(ls_a) # Result: [2, 2]
```

+ **不可变类型的浅拷贝**

Python所有单值变量及元组、字符串等序列变量不可变，取值的改变通过创建新对象实现。整型变量`b`重新赋值时，引用改为指向储存"2"的新对象，`a`仍然指向储存"1"的旧对象。因此不可变类型不会因为浅拷贝误改变原变量的值。

```python
a = 1
b = a # Shallow copy
b = 2
```

标准库`copy`提供了直观的浅拷贝函数`copy()`和深拷贝函数`deepcopy()`

### 作用域 Scope

+ **关键词**：`global`、`local`

定义的变量只在一定的尺度下有效，

+ **函数访问全局变量**


+ **内函数**





### 类型转换 Type Conversion



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

数值型变量有三种：整型`int`、浮点型`float`、复数`complex`。与C++、Java等语言不同的是，Python中没有为数值变量设置不同精度的类型，每种数值变量的精度是统一的。

```python
x = 4
y = -1.5
c1 = 1 - 7j
c2 = complex(x, y)
```

> [!hint] 数值型通用运算
> + **四则运算**：`+`（加）、`-`（减）、`*`（乘） 、`/`（除）
> + **指数**：`**` 或 `pow(x, y)`
> + **绝对值**：`abs(x)`	
> + **共轭**：`x.conjugate()`

### 整型 Integer




> [!hint] 整型运算
> + **求商及余数**：`//`（商）、`%`（余数）、`divmod(x, y)`（商及余数）
> + **比特运算**：
>	+ 按位逻辑：`&`（与）、`|`（或）、`~x`（取反）、`^`（异或）
>	+ 比特移位：`x<<n`（左移`n`位）、`x>>n`（右移`n`位）

### 浮点型 Float


### 复数 Complex






### 序列 Sequence

+ **参考**：[Doc](https://docs.python.org/3/library/stdtypes.html#sequence-types-list-tuple-range)

Python有三种序列型变量，**列表**`list`、**元组**`tuple`、**数列**`range`，其中数列一般用在[[#循环 Loop|循环语句]]，很少单独使用，元组适合存放固定的数据，数列适合存放经常需要改动的数据。

除上述三类序列型变量外，**字符串**`str`的运算以及处理函数（如分割、元素检测）与序列型变量类似，可以被认为是字符形式的序列结构。

元组和列表的元素之间类型可以不同

```python
# 元组 Tuple
my_tuple = ("red", "green", 12, "a", 3.3, "c")

# 列表 List
my_list = [12,]
 
```

> [!hint] 序列型通用操作（适用于列表、元组、数列、字符串）
> + **长度（元素个数）**：`len(s)`
> + **连接**：`s1 + s2`（首尾连接）、`s * n`（自身重复`n`次）
> + **极值**：`min(s)`、`max(s)`
> + **片段截取**：
>	+ 单个：`s[i]`（第`i`个元素）
>	+ 片段：`s[i:j]`（第`i`到第`j`个元素，不包含第`j`个）
>	+ 指定步长：`s[i:j:k]`（第`i`到第`j`个元素，步长为`k`，不包含第`j`个）
>	+ 倒数序号：`s[-i:-j]`（倒数第`i`到第`j`个元素，不包含倒数第`j`个）
> + **元素搜索**：
>	+ 检测：`x in s`（若含有`x`取真）、`x not in s`（若不含有`x`取真）
>	+ 序号：`s.index(x)`（输出`x`第一次出现的序号）
>	+ 计数：`s.count(x)`（输出`x`出现次数）

### 列表 List

+ **参考**：[W3schools](https://www.w3schools.com/python/python_lists.asp)

列表是最常用的序列类型。列表内的元素可以随意读写增删，与元组相比更加灵活，但也占用更多内存空间。

```python
my_list = ['ar', 1]
```

> [!hint] 列表操作
> + **增加元素**
>	+ 尾部添加：`s.append(x)`
>	+ 中间插入：`s.`

### 元组 Tuple





### 范围 Range





### 字符串 String

+ **参考**：[Doc](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)、[W3schools](https://www.w3schools.com/python/python_strings.asp)

Python所有字符变量都以字符串类型保存。字符串与序列类变量的性质相似，可以使用方括号`[]`访问或截取部分字符。

```python
my_str = "Hello World!"

```
Python自带不少用于处理字符串的函数和方法，复杂的字符串也可以使用正则表达式（标准库`re`）处理。

+ **字符串操作**
	+ **子串操作**
		+ 
	+ **字母处理**




### 字典 Dictionary





### 集合 Set


---
## 语法及逻辑 Syntax & Logics

这部分介绍Python的语法以及常用的逻辑判断语句

### 缩进 Indentation

Python的缩进用于代表语句的层次关系，因此会影响。函数定义、类定义、条件及循环语句的代码块必须使用**顿号加缩进**的形式标识

```python
class Example():
	def choose(self, x, y):
		if x == y:
			return True 
		else:
			return False
```


### 条件 Condition

+ **关键词**：`if`、`elif`、`else`、`break`

Python的条件语句


+ **三目运算符**

```python
isPos = True
a = 1 if isPos else 0
```


+ **If 语句**



+ **Match 语句** 






### 循环 Loop

+ **关键词**：`for`、`in`、`while`、`break`、`continue`
+ **可迭代类型**：`str`、`list`、`tuple`、`dict`、`set`


Python支持两种循环语句：遍历型（`for ... in`）、当型（`while`），

遍历型循环（`for ... in`）的循环变量遍历一个**可迭代对象**的元素

```
```


满足条件时持续迭代

### For 语句


### While 语句



### 异常处理 Exception Handling

+ **关键词**：`try`、`except`、`else`、`finally`



---
## 输入及输出 Input & Output


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


### 


---
## 代码封装 Encapsulation 

代码封装可以提高代码的复用率和可读性，与许多语言一样，Python提供了函数和类用于封装代码

### 自定义函数 Custom Functions

+ **参考**：
+ **关键词**：`def`、`return`

Python使用`def`关键词定义函数，函数可以有多个输入参数和多个输出返回值。

```python
def add_sub(a, b):
	x = a + b
	y = a - b
	return x, y

c, d = add_sub(1, 2)
print(c, d) # 3 -1
```

+ **类型标注**：可以使用以下格式标注输入参数和输出返回值的类型，实际上并不会运行类型检测，运行效果与前面的写法一样

```python
def add_sub(a: int, b: int) -> int:
	x = a + b
	y = a - b
	return x, y
```

+ **参数默认值**：函数的输入参数可以指定默认值，指定了默认值的参数在函数调用时可以不传入参数，此时参数使用默认值作为输入值

```python
def add_sub(a = 1, b = 2):
	x = a + b
	y = a - b
	return x, y

c, d = add_sub()
print(c, d) # 3 -1
```

+ **参数传递格式**
	+ 顺序：按参数的定义顺序赋值，可以省略参数名称
	+ 乱序：指定参数名称乱序赋值
	+ 混合：一但某个参数开始使用乱序赋值，后面的参数必须全部指定名称

下面的函数调用时，前两个参数使用顺序赋值，后三个参数使用乱序赋值

```python
def add(in1, in2, in3, in4, in5):
	return in1 + in2 + in3 + in4 + in5

r = add(1, 2, in4 = 4, in3 = 3, in5 = 5)
```

### 内函数 Nested Function

内函数是在一个函数内部定义的函数




### Lambda 表达式

+ **参考**：[Doc](https://docs.python.org/3/tutorial/controlflow.html#lambda-expressions)、




### 原生函数 Built-in Functions

+ **参考**：[Doc](https://docs.python.org/3/library/functions.html)

Python原生函数指可以直接使用，不需要导入的函数

| 函数       | 用途         |
| -------- | ---------- |
| `type()` | 检测标识符储存的类型 |
| `abs()`  |            |

### 自定义类 Custom Class








### 修饰器 Decorator



### 




---
## 库和模块 Package & Module

库和模块可以将实现了一定功能或算法的函数或类封装成可调用的

Python的库（Package）内部封装着

Python官方及社区共同维护一系列功能强大的库

### 模块导入 Import Modules





### 标准库 Standard Packages

+ **参考**：[文档](https://docs.python.org/3/library/index.html)

标准库是由Python官方维护的扩展库，默认受Python解释器支持，不需要另外安装，直接使用`import`导入即可使用

| 库名称及文档    | 主模块名称（简称） | 适用于       |     |
| --------- | --------- | --------- | --- |
| 🖥 os     | `os`      | 文件操作（底层）  |     |
| 🗂 shutil | `shutil`  | 文件操作（顶层）  |     |
| 🎰 random | `random`  | 伪随机数生成    |     |
| 📟 math   | `math`    | 调用数学函数    |     |
| ⏰ time    | `time`    | 时间记录与计算   |     |
| datetime  |           |           |     |
| 🐢 turtle | `turtle`  | 平面绘图      |     |
| 🏵 re     | `re`      | 正则表达式运算   |     |
| 🐘 abc    | `abc`     | 抽象类支持     |     |
| 📰 csv    | `csv`     | csv数据文件读写 |     |
| 🥜 copy   | `copy`    | 拷贝深浅控制    |     |

### 第三方库 Third-Party Packages

+ **库查询**：[Pypi / pip](https://pypi.org/)、[Anaconda / conda](https://anaconda.org/anaconda/repo?page=1)

第三方库指的是Python官方标准库以外的其他库，这些库通常以类和函数的形式提供封装好的算法和解决方案，涵盖各领域的通用算法以及软件工具的接口API，由各学术组织、基金会、公司维护

第三方库需使用`pip`或`conda`安装在当前Python环境后才能`import`

#### 专用库 Specialized Packages

| 库名称及文档                                                                       | 主模块名称（简称）           | 应用场景          | 学习笔记                            |
| ---------------------------------------------------------------------------- | ------------------- | ------------- | ------------------------------- |
| 🗃 [Numpy](https://numpy.org/doc/stable/user/index.html#user)                | `numpy` (`np`)      | 数组运算、数据处理     |                                 |
| 📈 [Matplotlib](https://matplotlib.org/stable/index.html)                    | `matplotlib`        | 数据绘图          |                                 |
| 🌊 [Seaborn](https://seaborn.pydata.org/)                                    | `seaborn`           | 高级数据绘图        |                                 |
| 📊 [Pandas](https://pandas.pydata.org/docs/user_guide/index.html#user-guide) | `pandas` (`pd`)     | 表格数据处理        |                                 |
| 🎰 [Scipy](https://docs.scipy.org/doc/scipy/reference/index.html#scipy-api)  | `scipy`             | 计算优化，信号处理     |                                 |
| 🌱 [Scikit-learn](https://scikit-learn.org/stable/)                          | `sklearn`           | 传统机器学习算法      |                                 |
| 🔦 [PyTorch](https://pytorch.org/docs/stable/index.html)                     | `torch`             | 机器学习库（偏科研）    | [[🔦 PyTorch 基本教程\| PyTorch]]   |
| ♨ [TensorFlow](https://www.tensorflow.org/api_docs/python/tf/all_symbols)    | `tensorflow` (`tf`) | 机器学习库（偏工业）    |                                 |
| 🍁 [Keras](https://keras.io/api/)                                            | `keras`             | 神经网络          |                                 |
| 🤗 Datasets                                                                  | `datasets`          | HF框架：数据集处理    |                                 |
| 🤗 Transformer                                                               | `transformer`       | HF框架：NLP、模型微调 |                                 |
| 🤗 Evaluate                                                                  | `evaluate`          | HF框架：训练评估     |                                 |
| ⛳ [Gymnasium](https://gymnasium.farama.org/)                                 | `gymnasium` (`gym`) | 强化学习环境测试框架    |                                 |
| 🦁 [PettingZoo](https://pettingzoo.farama.org/index.html)                    | `pettingzoo`        | 强化学习多智能体环境    |                                 |
| 🏀 [Stable Baselines](https://stable-baselines3.readthedocs.io/en/master/)   | `stable_baselines3` | 强化学习算法封装      |                                 |
| 🔫 [PyBullet](https://pybullet.org/wordpress/index.php/forum-2/)             | `pybullet` (`p`)    | 3D物理仿真器       |                                 |
| 🖼 [OpenCV](https://docs.opencv.org/4.x/d6/d00/tutorial_py_root.html)        | `cv2`               | 计算机视觉、图像处理    | [[OpenCV Python 基本教程\| OpenCV]] |
| 🎛 [Control](https://python-control.readthedocs.io/en/0.10.1/#)              | `control`(`ct`)     | 控制器设计、仿真、分析   |                                 |
| 🚢 [Simple PID](https://simple-pid.readthedocs.io/en/latest/user_guide.html) | `simple_pid`        | 简单PID控制器实现    |                                 |
| 🧊 [CVXPY](https://www.cvxpy.org/)                                           | `cvxpy`(`cp`)       | 凸优化           |                                 |
| 🧮 [Sympy](https://www.sympy.org/en/index.html)                              | `sympy`             | 数学表达式对象       |                                 |

+ **Top Down 分类学习**
	+ [Python 数据分析](📊%20Python%20数据分析.md)（🗃📈🌊📊🎰🌱）
	+ Python 神经网络（🔦♨🍁🤗）
	+ [Python 强化学习](⛳%20Python%20Farama%20强化学习工具链.md)（⛳🦁🏀）
	+ Python 机器视觉（🖼）
	+ [Python 控制系统](🐍%20Python%20控制框架.md)（🎛🚢）

#### 小型库 Small Packages

| 库名称及文档                                                                  | 主模块名称         | 应用场景    | 学习笔记 |
| ----------------------------------------------------------------------- | ------------- | ------- | ---- |
| 📝 [PrettyTable](https://ptable.readthedocs.io/en/latest/tutorial.html) | `prettytable` | 命令行表格打印 |      |
| 🚥 [Tqdm](https://tqdm.github.io/)                                      | `tqdm`        | 进度条     |      |
| attrs                                                                   |               |         |      |


### 自定义库 Custom Packages


