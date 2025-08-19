+ **参考**：[CPlusPlus](https://cplusplus.com/reference/vector/vector/)、[W3Schools](https://www.w3schools.com/cpp/cpp_vectors.asp)

向量是由C++标准库`<vector>`引入的一种长度可变的数组，有着一系列的封装好的操作函数，与C语言提供的默认数组相比更加好用，是C++最常用的标准容器之一。由于向量使用频率很高，这里特别用一个页面记录向量相关的特性和操作。

+ [定义](#定义) - [类成员](#类成员) · 
+ [读写](#读写)


---
## 定义

在代码中使用向量时，一定要引用标准库`<vector>`，如果代码中有`using namespace std;`，则可以省略命名空间前缀`std::`；向量的声明格式如下：

```c++
#include <vector>
int main()
{
	std::vector<int> my_vec;
}
```



### 类成员

要注意的是，向量声明为类成员变量时，不能直接用小括号调用向量类的构造函数，因为这种写法会被编译器误识别为函数的声明。可行的替代方法有几种：

+ 统一初始化（Uniform Initialization）
+ 在构造函数内定义
+ 定义后再赋值

```C++
class MyClass()
{
	// Wrong syntax would be misidentified as function declaration
	std::vector<int> my_vec(10, 0);
	
	// Corrected versions
	std::vector<int> my_vec = std::vector<int>(10, 0);
	std::vector<int> my_vec{10, 0};
	std::vector<int> my_vec = {10, 0};
}
```

---
## 读写






---
## 迭代