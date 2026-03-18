+ **另见** - 🐍 [Python文本读写]($02%20-%20🖥%20计算机科学%20Computer%20Science/$$%20-%20⌨️%20编程%20Programming/02%20-%20🐍%20Python/5%20-%20💾%20输入输出%20Input%20&%20Output/文本读写%20Reading%20and%20Writing%20of%20Text.md)

在C++中，文本读写是非常基础的功能，常用功能包括命令行的调试信息打印、参数输入，以及文本文件的读写。常用函数包括`cout`、`cin`、`getline`等

+ [相关类与函数](#相关类与函数) - 

+ [文本文件 -> 缓冲区](#文本文件%20->%20缓冲区)

---
## 相关类与函数

+ `cout` - 命令行输出文本
+ `cin` - 从缓冲区读入文本，直到遇到空格、换行符
+ `getline` - 从缓冲区读入一整行
+ `getchar` - 从缓冲区读入字符
+ `printf` - 继承自C语言的输出函数，少用
+ `scanf` - 继承自C语言的输入函数，少用

---
## 输出格式调整




---
## 检测文本结尾

```cpp
if (std::cin.peek() != EOF){
	std::cin >> a;
}
```



---
## 文本文件 -> 缓冲区

在ACM算法题目中，C++测试用例常以文本格式提供，考试者须使用`cin`读入测试数据。在本地测试时，手动输入数据到缓冲区很不方便，因此需要一些自动导入测试数据到缓冲区的方法，无须更改源代码中的`cin`语句即可实现自动测试。

> **文件读取** - 将文件`input.txt`读取到标准输入输出流`stdin`

```cpp
#include <fstream>
std::freopen("input.txt", "r", stdin)
```

> **字符串输入** - 将`cin`使用的寄存器重定向到字符输入流

```cpp
#include
string test_data = "1 2 3\n 4 5 6";
istringstream fakeinput(test_data);
cin.rdbuf(fakeinput.rdbuf());
```


