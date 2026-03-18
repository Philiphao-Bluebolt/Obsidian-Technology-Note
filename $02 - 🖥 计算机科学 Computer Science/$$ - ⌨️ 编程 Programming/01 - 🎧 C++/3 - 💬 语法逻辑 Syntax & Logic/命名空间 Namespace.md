+ **关键词**：`namespace`、`using`

命名空间是一种防止变量、函数、类重名的机制，调用命名空间下的成员必须使用命名空间的名称，C++中最常用的命名空间是标准库使用的`std`

```cpp
std::cout << a << std::endl;
```

> **创建命名空间** - 下面的例子里自定义了一个命名空间`circle`，调用命名空间`circle`里的函数和变量时必须在前面加上指定命令空间的标签`circle::`

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

> **省略命名空间名称** - 在某一作用域中使用`using namespace`语句可以在调用时省略命名空间的名称，但这种方法可能会导致不同命名空间之间的函数、变量名冲突

```cpp
#include <iostream>
using namespace std;
int main() {
	int a = 0;
	cout << a << endl;
}

```

