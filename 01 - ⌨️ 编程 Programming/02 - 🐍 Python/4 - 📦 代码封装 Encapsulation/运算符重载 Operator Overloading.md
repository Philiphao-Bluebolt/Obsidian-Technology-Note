Python的运算符重载可以通过重载类的特殊成员函数定义，下面这段例程展示了加号的重载

```python
class Vector:
	def __init__(self, input):
		self.vec = input
		
	# 重载加号 + 
	def __add__(self, other):
		result = Vector([0 for _ in range(len(self.vec))])
		for i in range(len(self.vec)):
			result.vec[i] = self.vec[i] + other.vec[i]
		return result
```


### 常用重载函数

- `__add__` → `+`
- `__sub__` → `-`
- `__mul__` → `*`
- `__truediv__` → `/`
- `__floordiv__` → `//`
- `__mod__` → `%`
- `__pow__` → `**`
- `__eq__` → `==`
- `__lt__` → `<`
- `__gt__` → `>`