+ **参考** - [Doc](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str)、[W3schools](https://www.w3schools.com/python/python_strings.asp)
+ **另见** - 🎧 [C++字符串](01%20-%20⌨️%20编程%20Programming/01%20-%20🎧%20C++/2%20-%20🎨%20变量运算%20Variables%20&%20Operations/字符串%20String.md)

Python中的字符串类型同时储存单个和多个字符，没有单个字符的变量类型。字符串与列表、元组等序列型容器的方法大致相同。复杂的字符串可以使用正则表达式（`re`标准库）识别

```python
my_str = "Hello World!"
```

---
## 常用操作

+  ``



---
## 字符串内嵌变量

方法一：使用`.format()`

```python
name = "Bob" 
age = 25 
print("My name is {} and I am {} years old.".format(name, age))
```

方法二：使用Formatted string literals（Python 3.6以上）

```python
name = "Alice"
age = 30
print(f"My name is {name} and I am {age} years old.")
```



