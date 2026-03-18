+ **参考** - [W3Schools](https://www.w3schools.com/cpp/cpp_iterators.asp)

C++中的迭代器是所有容器类型都拥有的一个特殊的成员对象，其行为与指针类似，可以用迭代器遍历容器里的元素。迭代器提供了一种遍历C++容器的统一方法，有利于泛型编程。

```
std::vector<int>::iterator 
std::string::iterator
```

+ **首尾**：容器的`begin()`和`end()`分别返回指向第一个元素和最后一个元素**之后**内存位置的
+ **类指针**：迭代器的使用方法与指针大致相同，`*`取值，`->`访问成员，`++/--`移位
+ **自动声明**：关键词`auto`可以替代掉冗长的迭代器类型声明

---
## 基本功能

+ **遍历元素**

```cpp
vector<int> arr = {1, 2, 3, 4};
for (auto iter = arr.begin(); iter != arr.end(); iter++){
	cout << *iter << " ";
}
```

+ **搜索元素**（`find()`也可以指定范围搜索）

```cpp
vector<int> arr = {1, 2, 3, 4};
int target = 3;
if (arr.find(target) != arr.end()){
	cout << "The element " << target << " exist!";
}
```

