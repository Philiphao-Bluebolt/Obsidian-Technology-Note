+ **关键词**：Material-aware 3D Reconstruction

1. 三维重建技术：发展历史、前沿技术、**技术瓶颈**
2. 已有三维重建技术**识别材质**的能力及方法
3. 基于触觉的三维重建技术

+ [历史](#历史)
+ [工具](#工具)
+ [前沿技术](#前沿技术)
+ [技术瓶颈](#技术瓶颈)
+ [材质识别](#材质识别)






---
## 历史

三维重建是基于二维图像重建现实中的三维物体或场景模型的技术或算法，是计算机视觉的其中一个研究分支。最早的三维重建技术与摄影测量法（Photogrammetry）有关，

现代的基于数字图像的三维重建技术最早出现于上世纪八十年代，当时的




+ **单一静止图像**

+ ****


+ **单目**

+ **双目视觉**

+ **结构光**

+ **SfM**（Structure from Motion，运动推断结构）是一种由


---
## 工具

+ Agisoft
+ PIX4D


---
## 前沿技术



## 材质识别

涉及材质识别的3D重建通常有以下几种解决方案

#### 材料语义分割

用带材料标注的**数据集**训练神经网络，使其能够自动对2D图像进行材料分割。将捕捉到的2D图像输入神经网络得到**逐像素的材料标注**图像，再结合深度图使用常规方法进行3D重建，将材料的标签映射到三维图的点云或者体素上。

使用这种方法的论文包括

+ [Simultaneous Material Segmentation and 3D Reconstruction in Industrial Scenarios](https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2020.00052/full)
+ [SAMa: Material-aware 3D selection and segmentation](https://arxiv.org/pdf/2411.19322)
+ 


#### 


---
## 技术瓶颈

#### 即时性差


####  





#### 数据依赖

---


---
## 数据集


+ CURet -
+ KTH-TIPS
+ Flicker Material
+ GeoMat
+ MINC (Materials in Context)
+ Wang's 4D light field material
+ 




---

> **[BeyondPixels: A Comprehensive Review of the Evolution of Neural Radiance Fields](https://arxiv.org/html/2306.03000v3)** ^e529f3

NeRF stands for Neural Radiance Field. It's a **fully-connected** neural network without convolutions that takes a 5D datas input



> **[Computer Vision Based 3D Reconstruction A Review](https://www.researchgate.net/publication/336887797_Computer_Vision_Based_3D_Reconstruction_A_Review)**