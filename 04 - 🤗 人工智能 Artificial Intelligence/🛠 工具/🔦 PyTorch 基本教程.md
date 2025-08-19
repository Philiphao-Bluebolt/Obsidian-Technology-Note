+ 参考：[文档](https://pytorch.org/docs/stable/index.html) | [教程](https://pytorch.org/tutorials/)

PyTorch是学术界流行的基于Python的深度学习框架，提供了优化的张量容器以及常用的网络、激活函数等基本工具，亦支持GPU并行运算加速。只需数行代码便可搭建起一个完整的神经网络

+ **基础**
	+ 📦️ **[张量](#张量%20Tensor)** - [创建](#创建%20Creating) · [运算](#运算%20Operation) · [访问](#访问%20Accessing) · 
	+ 🧮 **[数据库](#数据库%20Dataset)** - 
	+ [常用函数](#常用函数%20Function)
	+ [网络模块](#神经网络模块%20Neural%20Network%20Module)
+ ****


---
## 张量 Tensor

+ 参考：[张量类定义](https://pytorch.org/docs/stable/tensors.html) | [张量运算](https://docs.pytorch.org/docs/stable/torch.html)

```python
import torch
import numpy as np
```

PyTorch的数据结构基于一种**多维数组**容器——张量（Tensor），数据在其中排列成高维网格状结构，以便输入网络进行训练。张量有四个基本属性

+ **形状**：张量的维度以及不同维度的大小，以元组描述
+ **数据类型**：张量储存的数据类型，精度可选
+ **储存设备**：储存在CPU还是GPU上
+ **梯度**：运算时保存的微积分梯度信息

### 创建 Creating

> **普通数组转化**：支持Python数组和Numpy数组直接转化为张量，创建的张量形状、数据类型默认与原数组保持一致，数据类型（`dtype`）可以手动更改

```python
# 从Python数组创建
data = [[1, 2],[3, 4]]
dt = torch.tensor(data)

# 从Numpy数组创建
data = np.array([[1, 2],[3, 4]])
dt = torch.from_numpy(data)

# 手动修改数据类型
data = [[1, 2],[3, 4]]
dt = torch.tensor(data, dtype=torch.float64)
```

> **创建新张量**：创建与已有张量形状相同或者自定义形状类型的全零（`zeros`）、全一（`ones`）、随机（`rand`和`randint`）张量，其他类型还包括空张量（`empty`）、单位矩阵（`eyes`）

```python
dt = torch.tensor([[1, 2],[3, 4]])
shape = (3, 2)

# 形状拷贝（全零、全一、随机归一、随机整型）
zeros_t = torch.zeros_like(dt)
ones_t = torch.ones_like(dt)
rand_t = torch.rand_like(dt, dtype=float64)
randint_t = torch.randint_like(dt, low=0, high=10)

# 形状指定（全零、全一、随机归一、随机整型）
zeros_t = torch.zeros(size=shape)
ones_t = torch.ones(size=shape)
rand_t = torch.rand(size=shape, dtype=float64)
randint_t = torch.randint(size=shape, low=0, high=10)
```

> **属性查看**：输出张量的基本属性——形状、类型、储存设备（CPU/GPU）

```python
dt = torch.tensor([[1, 2],[3, 4]], device=torch.device('cuda'))

print(dt.shape)
print(dt.dtype)
print(dt.device)
```

### 运算 Operation

> **截取**：截取原张量的子块为新张量，格式为`[:, :, ]`，逗号分隔维度，取值范围不包含顿号后面序号，可使用负号代表倒数序号，留空代表从第一个开始/到最后一个

```python
dt = torch.tensor([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])

# tensor([[2, 3],
#         [6, 7]])
dt_blk = dt[0:2, 1:3]

# tensor([[ 5,  6,  7],
#         [ 9, 10, 11]]) 
dt_blk = dt[1:, :3]
```

> **拼接**：可以把多个张量拼在一起

```python

```

> **变形**：

> **逐元素运算**：大部分张量运算都属于逐元素运算，包括加减乘除，以及对数、指数、三角函数等一元初等函数

```python
dt1 = torch.tensor([1, 2][3, 4])
dt2 = torch.ones(size=(2, 2))

print(dt1+dt2)
print(dt1/dt2)
print(torch.sin(dt1))
```

> **统计类运算**：统计类运算包括取最大最小值、平均值、众数等，通常输出一个比原张量更小的张量储存结果

```
```




### 访问 Accessing

> **获取元素值**：先截取再用`item()`函数提取

```python
dt = torch.tensor([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])

# 两种写法都可以
element = dt[1, 2].item()
element = dt[1][2].item()
```


| 张量操作名称 | 相关方法          |     |
| ------ | ------------- | --- |
| 降维压缩   | `squeeze()`   |     |
|        | `unsqueeze()` |     |
|        | `expand()`    |     |
|        |               |     |

---
## 数据库 Dataset

数据是机器学习的燃料，所有模型的训练都建立在数据集之上。PyTorch提供了一些加载数据集的模块以及一些常用的测试用数据集。

```python
import torch
from torch.utils.data import Dataset
```








---
## 常用函数 Function

+ 模块：[torch.nn.functional](https://pytorch.org/docs/stable/nn.functional.html)

```python
import torch.nn.functional as F
```



---
## 神经网络模块 Neural Network Module

+ 模块：[torch.nn](https://pytorch.org/docs/stable/nn.html#linear-layers)

PyTorch将神经网络的隐藏层模块（如激活函数、卷积层）封装成模块，使构建复杂神经网络变为简单的搭积木

```python
from torch import nn
```


