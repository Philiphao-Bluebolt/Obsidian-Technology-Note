+ **文档**：[Python Documentation](https://docs.python.org/3/index.html) | [PEP 8 代码风格](https://peps.python.org/pep-0008/)
+ **教程**：[官方](https://docs.python.org/3/tutorial/index.html) | [W3schools](https://www.w3schools.com/python/) | [Geeksforgeeks](https://www.geeksforgeeks.org/python-programming-language-tutorial/) | [菜鸟](https://www.runoob.com/python/python-tutorial.html) | [WTF](https://github.com/satwikkansal/wtfpython)

Python是一门**解释型**面向对象脚本~~胶水~~高级编程语言，因其语法简单、扩展库丰富而受到广大开发者的欢迎，在数据分析、机器学习、应用开发等领域较为流行

+ 🐍 **[Python简介](#Python简介)**
+ ⚙️ **[环境配置](#环境配置%20Environment%20Setup)**
	+ 📚️ 模块与库 - 🌈 [常用库](🌈%20Python%20常用库列表.md) · 🍃 [Anaconda](🍃%20Anaconda.md) · 🧊 [Pip](🧊%20Pip.md) · 
	+ 🧼 集成 - ☄️ [VSCode](☄️%20VSCode%20使用教程.md#Python) · Pycharm · Spyder
+ 🎨 **[变量运算](#变量运算%20Variables%20&%20Operations)**
	+ 🧩 基本 - [布尔型](#布尔型%20Boolean) · [数值型](#数值型%20Value) ( [整型](#整型%20Integer) · [浮点型](#浮点型%20Float) · [复数](#复数%20Complex) )
	+ ☕ 序列 - [序列](#序列%20Sequence) ( [列表](#列表%20List) · [元组](#元组%20Tuple) · [范围](#范围%20Range) ) · [字符串](01%20-%20⌨️%20编程%20Programming/02%20-%20🐍%20Python/2%20-%20🎨%20变量运算%20Variables%20&%20Operations/字符串%20String.md)
	+ 组合 - [字典](#字典%20Dictionary) · [集合](#集合%20Set)
+ 💬 **[语法逻辑](#语法逻辑%20Syntax%20&%20Logics)**
	+ 语法 - [缩进](缩进%20Indentation.md) · [注释](注释%20Comment.md) · [赋值](#赋值%20Assignment) · [引用](引用%20Reference.md) · [作用域](01%20-%20⌨️%20编程%20Programming/02%20-%20🐍%20Python/3%20-%20💬%20语法逻辑%20Syntax%20&%20Logics/作用域%20Scope.md) · [类型转换](类型转换%20Type%20Conversion.md)
	+ 逻辑 - [条件](#条件%20Condition) · [循环](#循环%20Loop) · 递归 · [异常处理](#异常处理%20Exception%20Handling)
+ 📦 **[代码封装](#代码封装%20Encapsulation)**
	+ 函数 - [定义](定义函数%20Define%20Function.md) · [内函数](#内函数%20Nested%20Function) · [Lambda](#Lambda%20表达式) · 异步
	+ 类 - 自定义 ( 继承 · 实例化 ) ·
	+ 方法 - [修饰器](#修饰器%20Decorator) · 抽象 · 私有 · [运算符重载](运算符重载%20Operator%20Overloading.md)
+ 💾 **[输入输出](#输入输出%20Input%20&%20Output)**
	+ [文本](01%20-%20⌨️%20编程%20Programming/02%20-%20🐍%20Python/5%20-%20💾%20输入输出%20Input%20&%20Output/文本读写%20Reading%20and%20Writing%20of%20Text.md) 
	+ 命令行 - [表格](#表格%20Table) · [进度条](#进度条%20Progress%20bar) · 命令传参
	+ 文件 - 路径 · 纯文本 · 图片 · 其他

```python
if __name__ == "__main__":
	print("Hello World!")
```

+ 待归纳话题：条件语句、内函数

---
## Python简介



---
## 环境配置 Environment Setup

Python源代码通过解释器（Interpreter）执行，不需要预先编译成二进制机器码，因此只需要安装一个解释器即可在机器上运行基础的Python程序。实际上，为避免库版本冲突，Python程序员大多同时安装Anaconda等软件，使用虚拟环境管理不同项目的库





---
## 变量运算 Variables & Operations

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





### 字典 Dictionary





### 集合 Set


---
## 语法逻辑 Syntax & Logics

这部分介绍Python的语法以及常用的逻辑判断语句


+ 





### 条件 Condition

+ **关键词**：`if`、`elif`、`else`、`break`

Python的条件语句



> **If 语句**



> **Match 语句** 

Match语句是



> **三目运算符**

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

> **For 语句**


> **While 语句**


> **容器初始化**


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








### 类型转换 Type Conversion





### 异常处理 Exception Handling

+ **关键词**：`try`、`except`、`else`、`finally`



---
## 输入输出 Input & Output


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

### 定义函数 Define Functions

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

+ **类型标注**：可以使用以下格式标注输入参数和输出返回值的类型，运行效果与前面的写法一样。输入或输出的类型与标注不同并**不会**触发类型错误。

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




