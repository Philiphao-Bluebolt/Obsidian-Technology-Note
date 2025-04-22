+ 文档：[PyTorch](https://pytorch.org/docs/stable/index.html)
+ 教程：[官方](https://pytorch.org/tutorials/)

PyTorch是学术界流行的基于Python的深度学习框架，提供了优化的张量容器以及常用的网络、激活函数等基本工具，亦支持GPU并行运算加速。只需数行代码便可搭建起一个完整的神经网络

+ **基础工具**
	+ [[#张量 Tensor]]
		+ [[#创建张量]]
		+ [[#基础操作]]
	+ [[#常用函数 Function]]
	+ [[#神经网络模块 Neural Network Module]]

	+ [[#梯度计算 Gradient Calculation]]
+ **实战**
	+ [[#数据导入 Data Input]]

---
## 张量 Tensor

+ 模块：[torch.Tensor](https://pytorch.org/docs/stable/tensors.html)

PyTorch提供的张量是一种类似**多维数组**的数据容器，它可以将数据值排列成高维度的网格状结构，以便输入网络进行训练。其操作方法与数组类似




| 张量相关函数 |     |
| ------ | --- |
|        |     |
|        |     |
|        |     |
|        |     |


### 张量初始化 Tensor  

|     |     |
| --- | --- |
|     |     |

### 基础操作



| 张量操作名称 | 相关方法          |     |
| ------ | ------------- | --- |
| 读取维度规模 | `size()`      |     |
| 读取元素   | `item()`      |     |
| 降维压缩   | `squeeze()`   |     |
|        | `unsqueeze()` |     |
|        | `expand()`    |     |
|        |               |     |


```
```


### 数组类容器之对比






---
## 常用函数 Function

+ 模块：[torch.nn.functional](https://pytorch.org/docs/stable/nn.functional.html)（`import torch.nn.functional as F`）



---
## 神经网络模块 Neural Network Module

+ 模块：[torch.nn](https://pytorch.org/docs/stable/nn.html#linear-layers)（`from torch import nn`）

PyTorch提供了不同类型神经网络的隐藏层模块，包括，把构建神经网络的过程变为简单的搭积木。

```python
class
```


---
## 


---
## 梯度计算 Gradient Calculation



---
## 数据导入 Data Input 



---
## 