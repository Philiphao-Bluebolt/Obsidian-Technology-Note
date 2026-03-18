
+ [利用 enumerate() 获取元素编号](#利用%20enumerate()%20获取元素编号)
+ [使用 and 和 or 选择对象](#使用%20and%20和%20or%20选择对象)
+ [赋值语法 - 链式 · 并行 · 海象](#赋值语法%20-%20链式%20·%20并行%20·%20海象)
+ [循环语句也能接 else](#循环语句也能接%20else)
+ [链式比较与空容器自动转 False](#链式比较与空容器自动转%20False)
+ [关键词 del 删除容器元素](#关键词%20del%20删除容器元素)


---
## 利用 enumerate() 获取元素编号

在使用`for`循环时，可以使用`enumerate()`函数同时获取元素的值和编号；可以用`start`参数指定编号的初始值。

```python
arr = ["a", "b", "d"]
for num, i in enumerate(arr, start = 1):
	print(num, i)

# 等价于
for i in range(1, arr):
	print(num[i], i)
```

----
## 使用 and 和 or 选择对象

与C++不同，Python的`and`和`or`关键词并不会自动把运算对象转换为布尔值，而是会按从左到右的逻辑选择原本的运算对象输出。`or`会输出第一个为真（非空非零）的运算对象，`and`则输出第一个为假（空、零、`null`）的运算对象。

```python
a = []
b = [1, 2]
print(a or b) # 输出b [1, 2]
print(a and b) # 输出a []
```

这个特性可以用来避免一些边缘案例

```python
a = input
ans = (a or [-1]).pop()
# 等同于
ans = a.pop() if a else -1
```

---
## 赋值语法 - 链式 · 并行 · 海象

Python有几种很实用的赋值写法，如链式赋值（Chained Assignment）、并行赋值（Parallel Assignment）、海象赋值（Walrus Operator Assignment）

+ **链式赋值**：多个变量之间连续用赋值号连接，最右侧对象先解析，然后赋值顺序从左到右

```python
a = b = c = 3
# 等价于
temp = 3
a = temp
b = temp
c = temp
```

+ **并行赋值**：使用一个赋值号**同时**为多个变量赋值，没有前后顺序关系，通常用来提取容器内的元素。

```python
a, b = [1, 2]
a, b = b, a
```

+ **海象赋值**：允许变量在表达式中间赋值

```python
if (val := 1) > 0:
	print("+")
# 等价于
val = 1
if val > 0:
	print("+")
```

---
## 循环语句也能接 else

Python的`while`和`for`循环可以像`if`一样在后面接`else`语句块。循环语句的`else`仅在循环正常结束时执行，在使用`break`跳出循环时不执行。

```python
arr = [1, 4, 5, 6]
tar = 9
for i in arr:
	if i == tar: break
else:
	print("Not found!")
```

---
## 链式比较与空容器自动转 False

Python的条件语句有两个特性：链式比较和空容器自动转`None`；编写程序时利用这两个特性可以让条件语句更简约可读

+ **链式比较**：等式和不等式可以类似数学表达式一样连接成串；主流语言中只有Python拥有这个特性。

```python
if 1 < a == b <= 2: pass
# 等同于
if 1 < a and a == b and b <= 2: pass
```

+ **空容器自动转`False`**：所有的空容器、零值、关键词`None`在条件语句中自动转为`False`，在遍历容器时特别方便。
`
```python
arr = [1, 2, 3, 4]
while arr:
	print(arr.pop())
```

---
## 关键词 del 删除容器元素

Python中的`del`关键词统一了“删除变量”和“删除容器元素”的操作。在无需返回容器的被删除元素时，使用`del`代替`ctn.pop()`更简介

+ **删除容器元素**：使用`del`删除容器中的指定元素时效果与`pop()`类似，但不会返回被删除的元素值

```python
arr = [1, 2, 3, 4]
del arr[2]
print(arr) # [1, 2, 4]
```

+ **删除变量**：若使用`del`删除一个变量，变量的名称将在命名空间中被除名，变量无法在后续代码中访问

```python
var = 1
del var
print(var) # raise NameError
```
