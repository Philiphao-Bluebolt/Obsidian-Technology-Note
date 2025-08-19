+ **链接** - [原文](https://arxiv.org/pdf/2407.01349)

Panoptic Reconstruction

![](Pasted%20image%2020250731120259.png)

---
## 简介

Panoptic Reconstruction指的是包含**语义**和**实例**信息的3D重建过程，与Segmented Reconstruction最大的区别在于，前者不仅可以识别物体，还可以分辨同一类物体的不同实例。

![](Pasted%20image%2020250731112029.png)

相关研究：

> **Semantic Neural Fields 语义神经场** - NeRF的一类变体，可以在重建场景的几何构造同时，为场景里不同的物体打上语义标签。

+ **Semantic NeRF** - 在另外一条管线上对输入2D图像进行语义分割，再将有噪声的2D语义分割图融合为三维模型
+ **NeSF** - 直接将三维稠密场输入到一个3D语言分割模型，预测对应的语义场
+ **NIVLFF** - 

> **Panoptic Neural Fields 全知神经场** - 

+ **PNF** - 




> **Panoptic NeRF**

> **PVLFF**

> **SAM**

> **Grounded-SAM**
