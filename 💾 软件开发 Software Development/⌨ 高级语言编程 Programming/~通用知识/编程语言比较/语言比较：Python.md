
---
## 注释

```python
# Single Line

'''
Multi Line
'''
```

---
## 变量和运算

Python的变量本质上是对象，不需要声明，类型随意改变；运算可以用`**`表示二次方，加一运算符不支持`++`，可以用`+=`

```python
a = 1
b = 2
str = a
str = "Hello World"

a = b ** a
b += 1
```

---
## 分支

Python不支持`case`多分支语句

```python
if x < 1 and y > 2 or z != 0:
	pass
elif w = 1:
	pass
else:
	pass

```


---
## 循环

```python
for i in range(1, 10)
	pass
```



---
## 类

```python
class 
```

---
## 程序入口

Python的程序入口不是必须的，这种写法规范只是为了可读性

```python
if __name__ = "__main__":
	pass
```