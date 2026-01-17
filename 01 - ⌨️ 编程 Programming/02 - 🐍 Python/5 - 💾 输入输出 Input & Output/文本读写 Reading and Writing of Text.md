+ **另见** - 🎧 [C++ 文本读写](01%20-%20⌨️%20编程%20Programming/01%20-%20🎧%20C++/5%20-%20💾%20输入输出%20Input%20&%20Output/文本读写%20Reading%20and%20Writing%20of%20Text.md)

Python中的文本读写主要使用的是`sys.stdio`模块



---
## 命令行读写

+ `sys.stdin` - 输入缓存区
+ `input()` - 逐行读入

```python
import sys 

for lines in sys.stdin:
	
```



---
## 文本文件读写


### 直接读取

`with`语句块可以自动处理文件的打开与关闭，文件类的`read()`方法自动将文本内容写入字符串。

```python
import os
import sys

os.chdir(os.path.dirname(__file__))
with open("data.txt", "r") as file:
	data_str = file.read()
	
print(data_str)
```

也可以把文本内容写到输入缓存区`sys.stdin`




### 命令行管线

用Linux命令行的输入运算符`<`可以将文本文件中的内容读入Python程序的缓存区，实现用文本文件模拟命令行手动输入的效果。

```bash
python input.py < data.txt
```
