Python内置了很多字符串处理相关的函数可以调用，不需要自己实现

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

---
