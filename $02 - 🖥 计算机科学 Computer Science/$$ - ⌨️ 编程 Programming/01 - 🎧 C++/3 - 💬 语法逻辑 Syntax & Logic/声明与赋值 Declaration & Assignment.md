+ **关键词** - `auto`

C++中的变量与对象在使用前必须声明其类型，指导编译器提前为变量值的储存分配一定的内存空间。此外，声明语句还可以指定变量的特殊属性，如常量、静态、指针、引用。已声明但未赋值的变量，值是不确定的。

```cpp
int num = 1;
MyClass my_obj;
```

+ **普通声明**

```cpp
int num;
std::vector<double> arr;
MyClass my_object; 
```

+ **引用**

```cpp
int& a = num;
vector<double>& arr_r = arr;
MyClass
```

+ **指针**

```
```