+ **文档**：[CPlusPlus](https://cplusplus.com/reference/)、[DevDocs](https://devdocs.io/cpp/)
+ **教程**：[W3schools](https://www.w3schools.com/cpp/)

C++是一门编译型面向对象语言，其语法规则基于C语言，是后者的超集。ABI是C++面临的主要问题

+ ⚙ **环境配置**（总览）
	+ 🛠 编译器：CMake | Visual C++ | MinGW | Ninja
	+ 🧼 集成：Visual Studios | VS Code
+ 📐 **变量及运算**（总览 | 声明 | 赋值 | 作用域 | 动态分配）
	+ 🧩 单值：布尔型 | 整型 | 浮点型 | 字符型
	+ ☕ 容器：数组 | 字符串 | 向量 | 列表 | 栈 | 队列（双端）| 映射（无序）| 集合（多集合）
	+ 🧱 整合：结构体 | 枚举型
	+ 💉 指向：引用 | 指针 | 智能指针 | 迭代器
+ 💬 **语法及逻辑**（总览）
	+ 📜 语法：[命名空间](命名空间%20Namespace.md) | 
	+ ⚖ 判断：条件 | 循环 | 基本算法
+ 💾 **输入及输出**
	+ 💻 命令行：
	+ 📁 文件：
+ 📦 **函数**（总览）
	+ 标准库：
	+ ☎ 自定义：定义 | 传参 | 
+ 🎮 **面向对象**（总览）
	+ 💊 基本：自定义 | 继承 | 抽象 | 访问权限
	+ 🚀 方法：友元 | 
+ 🗃 **库与模块**
	+ 🎛 标准库：
	+ ✂ 第三方库：


```C++
#include <iostream>

int main() {
	std::cout << "Hello World" << "\n";
}
```

---
## 数组 Array

C++的数组继承自C语言，以连续的内存地址储存在栈中，因此长度不可变。

```python
int a[5] = {1, 3, 5, 4, 2};
```


---
## 字符串 String


---
## 向量 Vector

+ **参考**：[CPlusPlus](https://cplusplus.com/reference/)、[W3Schools](https://www.w3schools.com/cpp/cpp_vectors.asp)
+ **声明**：`vector<type>`

向量是由标准库`<vector>`引入的长度可变数组，是C++最常见的容器之一。

向量的声明




```c++
#include <vector>
int main()
{
	std::vector<int> my_vec;
}
```







向量的基本操作

+ 声明
	+ 一维：`vector<int>`、`vector<string>`
	+ 多维：`vector<vector<int>>`
+ 迭代器
	+ 
	+ 插入：




---
## 引用 Reference




---
## 指针 Pointer




---
## 命名空间 Namespace

+ **关键词**：`namespace`、`using`

命名空间是一种防止变量、函数、类重名的机制，调用命名空间下的成员必须使用命名空间的名称，C++中最常见的命名空间是标准库的`std`

```cpp
std::cout << a << std::endl;
```

下面的例子里自定义了一个命名空间`circle`，调用命名空间`circle`里的函数和变量时必须在前面加上指定命令空间的标签`circle::`

```cpp
namespace circle {
	double r;
	double area(double radius){
		return 3.1415629 * radius * radius;
	}
}

int main(){
	circle::r = 10;
	answer = circle::area(circle::r);
	return 0;
}

```

在全局作用域中使用`using namespace`语句可以在调用时省略命名空间的名称，这种方法可能会导致函数、变量名冲突，因此不建议使用

+ **正常版**

```cpp
#include <iostream>
int main() {
	int a = 0;
	std::cout << a << std::endl;
}
```

+ **省略版**

```cpp
#include <iostream>
using namespace std;
int main() {
	int a = 0;
	cout << a << endl;
}

```



---
## 库与模块 Libraries & Packages


### 标准库 Standard Library

+ **列表**：[Standard Library Reference](https://cplusplus.com/reference/)

| 库名称           | 功能     |     |
| ------------- | ------ | --- |
| algorithm     | 基本算法   |     |
| vector        | 引入向量容器 |     |
| unordered_map |        |     |
| limit         |        |     |
| math          |        |     |
|               |        |     |


### 第三方库 Third-Party Packages

| 库名称                                         | 应用场景    |
| ------------------------------------------- | ------- |
| Ceres                                       |         |
| G2o                                         | 非线性优化   |
| OpenCV                                      | 计算机视觉   |
| Eigen                                       | 矩阵优化    |
| PCL                                         | 点云处理    |
| Glog                                        | 应用层日志记录 |
| [Armadillo]()                               | 线性代数    |
| [Dlib](https://dlib.net/)                   | 机器学习    |
| [PyTorch C++](https://pytorch.org/cppdocs/) | 机器学习    |
| Robotics Library                            |         |
| OCS2                                        |         |

