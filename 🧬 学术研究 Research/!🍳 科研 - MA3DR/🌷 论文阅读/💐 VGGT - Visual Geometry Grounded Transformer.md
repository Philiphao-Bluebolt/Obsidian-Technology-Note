+ **链接**：[Github](https://vgg-t.github.io/)

这篇文章是CVPR 2025的最佳论文，提出了一种用于3D处理任务的新模型——VGGT。VGGT使用Transformer架构作为Backbone，在大部分的3D任务上的性能超越了现有模型

![](Pasted%20image%2020250711162901.png)

+ **论文阅读**
	+ **[简介](#简介)** - [研究贡献](#研究贡献) · [相关研究](#相关研究)
	+ **[方法论](#方法论)** - [问题定义](#问题定义) · [Backbone](#Backbone) · [Head](#Head)
	+ **[模型训练](#模型训练)** - [损失函数](#损失函数) · [数据集](#数据集)
	+ **[展望](#展望)** - [不足](#不足)
+ **代码分析**
	+ [项目架构](#项目架构)


---
## 简介

### 研究贡献

1. **提出VGGT模型**：这是一种前向的Transformer模型。可以在**数秒之内**预测单张或多张输入2D图像的所有关键3D属性，包括相机内参和外参、点地图（Point Map）、深度图（Depth Map），以及3D点在不同图像之间的跟踪（3D Point Tracks）；

2. **无需后优化处理**：与之前的3D大模型不同，VGGT生成的内容可以直接使用，不需要任何的优化处理；

3. **BA优化后效果拔群**：如果对生成结果进行光束平差优化（Bundle Adjustment），VGGT的生成质量在所有3D相关领域超越一切现有模型


### 相关研究

1. **运动恢复结构**：运动恢复结构（Structure from Motion）是经典的计算机视觉问题，其目标是从一组静态场景的照片推测相机的位置以及生成场景的稀疏3D点云。传统的算法包含图像匹配、三角化和光束平差三步，近年来技术路线逐渐转移至神经网络。

2. **多视觉立体视角**：多视觉立体视角（Multi-view Stereo）是从一组重叠的照片以及相机参数重建场景的稠密几何结构的技术，分为三大类：Handcrafted、全局优化、基于学习

3. **点跟踪**：点跟踪是在一组图像或视频之中，在所有帧中找到选定点的一种技术。

---
## 方法论

### 问题定义

本质上VGGT是一个函数，将$N$张RGB图像组成的序列映射到$N$组3D特征上，这些特征包括相机内外参数、深度图、点位图和一个用于点追踪的网格
$$f\{(I_i)_{i=1}^N\}=(g_i,D_i,P_i,T_i)_{i=1}^N$$
+ $(I_i)_{i=1}^N$ - 输入的$N$张RGB图像$I\in \mathbb{R}^{3\times H \times W}$
+ $g_i$ - 生成的九个相机内外参数（$g_i\in \mathbb{R}^9$）
+ $D_i$ - 生成的深度图（$D_i\in \mathbb{R^{H\times W}}$）
+ $P_i$ - 生成的点位图（$P_i\in \mathbb{R^{3\times H \times W}}$）
+ $T_i$ - 生成的点追踪网格（$T_i\in \mathbb{R^{C\times H\times W}}$）

### Backbone

VGGT使用了一个略微改动过的Transformer模型作为特征提取的Backbone，新引入了称为**交替注意力**（Alternating Attention）的机制，可以让Transformer交替地关注每一帧或全局所有输入。

+ **逐帧自注意力**（Frame-wise self-attention）仅关注一帧内（Intraframe）的Token
+ **全局自注意力**（Global self-attention）则关注所有（Interframe）的Token。

在VGGT内部，逐帧自注意力层和全局自注意力层交替链接，组成24对注意力层。这些注意力层只包括自注意力，不包含交叉注意力。

每一张输入的图像$I$使用**DINO网络**分成$K$块（Patch）并转化为Token，$N$张输入图像的Token依次输入Transformer中进行处理。

### Head

VGGT使用了不同的模型实现了相机参数、深度图、点位图的生成和点的跨帧追踪。这些生成的特征以**第一张图**$I_1$的相机坐标轴为参考系。

+ **图像相机参数** $\hat{g}_{i=1}^N$：输出Tokens经过自注意力层$\times 4$ + 线性层映射到参数向量

+ **密集特征预测**：Backbone输出的Tokens先用**DPT层**转化为密集特征图（Dense Map），然后用一层卷积层映射到深度图$D_i$和点地图$P_i$，也会输出跟踪特征图$T_i$。这里的密集是“逐像素”的意思

+ **点跟踪**：$T_i$密集特征图输入到**CoTracker2**模型架构。与**VGGSfM**类似，不考虑图像之间的时间顺序。

---
## 模型训练

### 损失函数




### 数据集

VGGT训练用的数据集规模大、多样性广，这一点与**MASt3R**类似。用到的数据集里面，包含室内和户外的图片、合成和真实的照片，不同数据集里的图像三维信息也是通过不同的方法得到，包括传感器直接采集、引擎合成、SfM。



### 



---
## 展望

### 不足

在Huggingface上测试VGGT，似乎并不能很好地重建反射或折射表面



---
## 项目架构

下面列出VGGT项目中主要的文件

+ **VGGT**
	+ 📁 **`vggt`** - VGGT模型的主要源代码，实现Backbone、Head、Layer等核心模块
		+ 📁 **`models`** - 
			+ 🐍 **`vggt.py`** - 
			+ 🐍 `aggregator.py` - 
		+ 📁 `dependency` - 
			+ 📁 `track_modules` - 
		+ 📁 `heads` - 
		+ 📁 `layers` - 
		+ 📁 `utils` - 
	+ 📁 `training` - 
	+ 📁 `examples` - 测试用输入图片和视频
	+ 🐍 `demo_colmap.py`
	+ 🐍 `demo_gradio.py`
	+ 🐍 `demo_viser.py`
	+ 📃 `requirements.txt` - 运行VGGT本体的依赖库
	+ 📃 `requirements_demo.txt` - 运行三个Demo测试及本体所必需的依赖库

### 