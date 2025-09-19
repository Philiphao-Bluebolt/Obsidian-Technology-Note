+ **文档**：[CPlusPlus](https://cplusplus.com/reference/)、[DevDocs](https://devdocs.io/cpp/)
+ **教程**：[W3schools](https://www.w3schools.com/cpp/)、[菜鸟](https://www.runoob.com/cplusplus/cpp-tutorial.html)

C++是一门编译型面向对象语言，工业界最常用的编程语言之一，具有运行速度快、占有资源少的优点。C++也是C家族成员，基本兼容C语言的语法。

+ ✨ [**C++简介**](#C++%20简介)
+ ⚙️ [**环境与配置**](#环境与配置%20Environment%20Setup)
	+ 🛠 **[编译](#编译%20Compile)** - [CMake](CMake.md) · G++ · Visual C++ · MinGW · Ninja
	+ 🧼 **[集成](#集成%20IDE)** - Visual Studios · VS Code
	+ 🌈 **[框架与库](#框架与库%20Frameworks%20&%20Libraries)** - [常用库](🌈%20C++%20常用库列表.md)
+ 🎨 **[变量与运算](#变量与运算%20Variables%20&%20Operations)**
	+ 🧩 **[基本](#基本类型%20Basic%20Types)** - 布尔型 · 整型 · 浮点型 · 字符型 · 枚举型
	+ ☕ **[容器](#容器%20Containers)** - 字符串 · [向量](向量%20Vector.md) · 数组 · 列表 · 栈 · 队列 ( 双端 ) · 映射 ( 无序 · 多 ) · 集合 ( 无序 · 多 )
	+ 💉 **[属性](#类型属性%20Type%20Property)** - 引用 · 指针 · 智能指针 · 常量 · 静态
+ 💬 **[语法与逻辑](#语法与逻辑%20Syntax%20&%20Logic)**
	+ ✒️ **[语法](#语法%20Syntax)** - 注释 · [声明](声明与赋值%20Declaration%20&%20Assignment.md) · [赋值](声明与赋值%20Declaration%20&%20Assignment.md) · 类型转换 · [作用域](作用域%20Scope.md) · [命名空间](命名空间%20Namespace.md) · 动态分配
	+ 🌀 **[控制流](#控制流%20Control%20Flow)** - [条件](条件语句%20Condition%20Syntax.md) · [循环](循环语句%20Loop%20Syntax.md) · [递归](递归%20Recursion.md) · [异常处理](异常处理%20Handling%20Exception.md)
+ 📦 **[代码之封装](#代码之封装%20Code%20Encapsulation)**
	+ ☎️ **[函数](#函数%20Function)** - 传参 · Lambda
	+ 🎁 **[面向对象](#面向对象%20Object%20Oriented)** - 成员 · [权限](访问权限修饰器%20Access%20Modifier.md) · 继承 · 抽象 · 构造 ( 初始化表 ) · 析构 · 运算符 · 只读 · 友元
	+ 📑 模块 - 头文件
+ 💾 **[输入与输出](#输入与输出%20Input%20and%20Output)**
	+ 💻 **[命令行](#命令行%20Command%20Line)** - 缓存区
	+ 📂 **[文件](#文件%20Files)** - 
+ 


未分类话题：模板（泛型编程）、内存管理、多线程、输入输出流、预处理语句

---
## C++ 简介

C++编写的“Hello World”程序

```C++
#include <iostream>
int main() {
	std::cout << "Hello World" << "\n";
}
```

C++语言标准目前由国际标准化组织ISO编写及维护，每三年左右更新一次标准，加入新的功能与语法。标准版本以年份命名，如“C++98”、“C++11”，工业界常用版本一般比最新版早**5-8年**。目前（2025年）广泛使用的标准为**C++17**

ABI是C++面临的主要问题


---
## 环境与配置 Environment & Setup


### 编译 Compile



### 集成 IDE




### 框架与库 Frameworks & Libraries

C++的库分为两种——标准库与第三方库，前者是C++标准的一部分，包含C标准库，默认受编译器支持；后者则是由软件基金会、企业等维护的非官方框架。有不少C++第三方库，如OpenCV、PCL，同时支持Python、Java等其他工业界常用语言。

C标准库是C++标准库中继承自C语言的部分，以头文件形式定义（如`math.h`）且没有命令空间。C++标准提供了这些库的优化版本（如`cmath`）。调用时尽量使用优化版本

> 库的导入：

```C++
#include <iostream>
#include <cmath>
```

常用的C++库参见：🌈 [常用库](🌈%20C++%20常用库列表.md)




---
## 变量与运算 Variables & Operations


### 基本类型 Basic Types




### 容器 Containers

+ **参考** - [CPlusPlus](https://en.cppreference.com/w/cpp/container.html)

C++标准库中的容器是常见数据结构的实现，一共有4大类共16种：

+ 序列（Sequence）：向量、数组、列表、双端队列
+ 关联（Associative）：映射、多映射、集合、多集合
+ 无序（Unordered）：无序映射、无序多映射、无序集合、无序多集合
+ 转换（Adaptor）：栈、队列、优先队列

字符串本质上是

| 标准库    | 容器   | 相当于 | 类型  | 实现  |
| ------ | ---- | --- | --- | --- |
| string | 字符串  |     |     |     |
| vector | 向量   |     |     |     |
| list   | 列表   |     |     |     |
| stack  | 栈    |     |     |     |
| queue  | 队列   |     |     |     |
| deque  | 双端队列 |     |     |     |
| map    | 映射   |     |     |     |
|        | 无序映射 |     |     |     |
|        | 集合   |     |     |     |
|        | 无序集合 |     |     |     |
|        | 多集合  |     |     |     |









C++的双引号`""`表示字符串，单引号`''`表示字符


### 类型属性 Type Property



---
## 数组 Array

C++的数组继承自C语言，以连续的内存地址储存在栈中，因此长度不可变。

```python
int a[5] = {1, 3, 5, 4, 2};
```


---
## 字符串 String

+ **参考**：
+ ****



---
## 语法与逻辑 Syntax & Logic


### 语法 Syntax

C++的语法风格与C语言相似，较为传统。语句之间用分号`;`隔开，换行位置与缩进长度对编译没有影响。





### 控制流 Control Flow

控制流指的是程序运行时语句的执行顺序，常见的有四种控制流程结构：顺序执行、条件分支、循环、子程序。递归是一种特殊的控制流，是子程序（函数）与条件分支的结合。

+ [条件语句 Condition Syntax](条件语句%20Condition%20Syntax.md)
+ [循环语句 Loop Syntax](循环语句%20Loop%20Syntax.md)
+ [递归 Recursion](递归%20Recursion.md)
+ [异常处理 Handling Exception](异常处理%20Handling%20Exception.md)


---
## 代码之封装 Code Encapsulation


### 函数 Function



### 面向对象 Object Oriented

面向对象是C++的重要功能，其基本思想是将**数据变量**与对它们的**操作流程**统一封装在称为**类**的框架下，以提高程序代码的可复用性与扩展性。

值得一提的是，C++中的**结构体**（Struct）可以定义成员函数以及被继承，与类的功能基本一致，唯一区别是结构体中的成员默认公有（Public）。约定俗成的代码习惯是，使用结构体储存没有复杂逻辑的POD数据，使用类封装复杂的面向对象逻辑。








---
## 输入与输出 Input and Output


### 命令行 Command Line





### 文件 Files