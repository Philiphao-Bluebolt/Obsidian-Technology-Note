命名空间是一种防止变量、函数、类重名的机制，调用命名空间下的成员必须使用命名空间的名称

```cpp
namespace_name::member_name
```

下面是一个使用范例，可以看到，无论是修改命名空间`simple_example`里变量`r`的值还是调用它的函数，前面都要加上`simple_example::`

```cpp
namespace simple_example
{
	double r;
	double calculate_circle_area(double radius)
	{
		return 3.1415629 * radius * radius;
	}
}

int main()
{
	simple_example::r = 10;
	answer = simple_example::calculate_circle_area(simple_example::r);
	return 0;
}

```

C++中最常见的命名空间是标准库的`std`

```cpp
std::cout << a << std::endl;
```

当然，我们可以通过使用`using namespace`语句在调用时省略掉命名空间的名称，但是这种方法可能会导致函数、变量名冲突，因此不建议使用

```cpp
using namespace std;

int main()
{
	int a = 0;
	cout << a << endl;
}

```