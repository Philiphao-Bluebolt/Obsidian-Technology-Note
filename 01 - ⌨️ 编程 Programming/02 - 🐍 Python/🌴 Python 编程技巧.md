
+ [循环语句也能接 else](#循环语句也能接%20else)
+ [链式比较与空容器自动转 False](#链式比较与空容器自动转%20False)
+ [关键词 del 删除容器元素](#关键词%20del%20删除容器元素)


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
