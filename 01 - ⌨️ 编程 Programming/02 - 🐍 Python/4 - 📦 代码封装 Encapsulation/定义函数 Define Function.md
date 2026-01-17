+ **参考**：
+ **关键词**：`def`、`return`

Python使用`def`关键词定义函数，函数可以有多个输入参数和多个输出返回值。

```python
def add_sub(a, b):
	x = a + b
	y = a - b
	return x, y

c, d = add_sub(1, 2)
print(c, d) # 3 -1
```

+ **类型标注**：可以使用以下格式标注输入参数和输出返回值的类型，运行效果与前面的写法一样。输入或输出的类型与标注不同并**不会**触发类型错误。

```python
def add_sub(a: int, b: int) -> int:
	x = a + b
	y = a - b
	return x, y
```

+ **参数默认值**：函数的输入参数可以指定默认值，指定了默认值的参数在函数调用时可以不传入参数，此时参数使用默认值作为输入值

```python
def add_sub(a = 1, b = 2):
	x = a + b
	y = a - b
	return x, y

c, d = add_sub()
print(c, d) # 3 -1
```

+ **参数传递格式**
	+ 顺序：按参数的定义顺序赋值，可以省略参数名称
	+ 乱序：指定参数名称乱序赋值
	+ 混合：一但某个参数开始使用乱序赋值，后面的参数必须全部指定名称

下面的函数调用时，前两个参数使用顺序赋值，后三个参数使用乱序赋值

```python
def add(in1, in2, in3, in4, in5):
	return in1 + in2 + in3 + in4 + in5

r = add(1, 2, in4 = 4, in3 = 3, in5 = 5)
```
