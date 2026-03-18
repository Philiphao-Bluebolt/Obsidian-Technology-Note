
+ **August** -
+ **July** - [28](#^4fff02) · [9](#^984390)
+ **June** - [20](#^9b2f50) · [19](#^9d3091) · [18](#^030ebd) · [14](#^d86060) · [13](#^87c8d7) · [11](#^0064e3) · [10](#^5a172d) · [8](#^305646) · [6](#^f25d12)
+ **May** - [28](#^36bea9) · [27](#^ec614e)



---

> [**VTLA: Vision-Tactile-Language-Action Model with Preference Learning for Insertion Manipulation**](https://arxiv.org/pdf/2505.09577) ^4fff02





> **[VGGT: Visual Geometry Grounded Transformer](https://vgg-t.github.io/)** ^984390

这篇是2025 CVPR的最佳论文



> A Survey on Vision-Language-Action Models for Embodied AI


> **[FusionSense: Bridging Common Sense, Vision, and Touch for Robust Sparse-View Reconstruction](https://arxiv.org/html/2410.08282v1?utm_source=chatgpt.com)** ^9b2f50



> **[Tactile sensors: A review](https://www-sciencedirect-com.remotexs.ntu.edu.sg/science/article/pii/S026322412401217X)**



> **[A Touch, Vision, and Language Dataset for Multimodal Alignment](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://arxiv.org/pdf/2402.13232)** ^9d3091




> **[Review of Bioinspired Vision-Tactile Fusion Perception (VTFP): From Humans to Humanoids](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9925051)** ^030ebd



> **[Experimental Investigation of Surface Identification Ability of a Low-Profile Fabric Tactile Sensor](https://ieeexplore.ieee.org/document/6385538)** ^d86060

论文作者制作了一台基于滑动触觉传感的材质识别系统。



> **[A Comprehensive Review of Vision-Based 3D Reconstruction Methods](https://www.mdpi.com/1424-8220/24/7/2314)** ^87c8d7






> **[Material Recognition Using Tactile Sensing](https://www-sciencedirect-com.remotexs.ntu.edu.sg/science/article/pii/S0957417417307273)** ^0064e3

一篇写作质量非常高的论文！甚至有和人类组的对比

材质识别三大传感模态：视觉、触觉、听觉

人类认识一个物体的方式首先是视觉，视觉可以让我们知道这个物体的几何外形，也可以





> **[Computer Vision Based 3D Reconstruction A Review](https://www.researchgate.net/publication/336887797_Computer_Vision_Based_3D_Reconstruction_A_Review)** ^5a172d

这篇文章是对基于视觉的3D重建技术的综述。文章将3D重建技术按所需的输入图像类型分为四类：单一静止图像、RGBD静止图像、多张RGBD图像、视频



> **[Simultaneous Material Segmentation and 3D Reconstruction in Industrial Scenarios](https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2020.00052/full)** ^305646

这篇文章介绍了一种基于神经网络的3D重建和材质识别方法，用于核废料的材质识别。系统分为两部分：单帧材料分割和语义3D重建。首先，将RGBD相机捕捉到的RGB图像输入神经网络进行逐像素的材料分割，再与深度图匹配生成3D点云

综述部分介绍了一些材质图片的数据集：CURet、KTH-TIPS、Flicker Material、GeoMat，这五个数据集仅有图片标签；MINC提供了逐像素的材质类型标签。



> **[3DGS.zip: A survey on 3D Gaussian Splatting Compression Method](https://arxiv.org/pdf/2407.09510)** ^f25d12

这是一篇针对3DGS方法的综述，

优势：

+ 可处理复杂的视觉效果（变视角光照、透明表面）
+ 可修改，可以与其他3D格式共存
+ 支持GPU在线3D渲染

Compress vs Compact

> **[A Multi-modal Approach to Continuous Material Identification through Tactile Sensing](https://arxiv.org/pdf/2311.03090)** ^36bea9

这篇论文提出了一种同时利用振动和热（Thermal）数据的**多模态物体材质识别**方法，先对触觉传感器收集的振动和热数据进行预处理，再使用**递归贝叶斯估计**完成分类任务。

实验中使用的数据由**SynTouch BioTAC**触觉传感器采集，这种传感器模拟人的触觉，可以同时检测压力、形变、振动、温度以及热通量。传感器由一个内部加热源、中间的软胶和外围的橡胶软膜构成，软膜上的阻抗传感器阵列可以感知形变，压力和振动信息通过压力传感器检测。

论文中对振动与热两种原始数据分别进行处理

+ **振动信号**：振动信号一般是压力信号的高频部分，FFT提取振动信号的频谱，使用PCA（主成分分析）对高维的频谱信息进行降维，根据频谱特征对材料进行分类。

+ **温度和热信号**：通过阻抗传感器的数据估算大致的接触面积，用温度、平均热通量、接触面积估算接触材料的热导率；对热通量随时间的变化函数进行线性回归，得到回归斜率和回归误差。用热导率、斜率、误差三个计算值描述材料的热特性特征。

材料分类使用贝叶斯估计


> **[BeyondPixels: A Comprehensive Review of the Evolution of Neural Radiance Fields](https://arxiv.org/html/2306.03000v3)** ^ec614e

这是一篇成稿于2023年，讨论NeRF三维重建技术原理和最新成果的综述文章，详细介绍了NeRF的网络结构、优缺点、损失函数、训练数据集、评估指标，以及其他特性，对近年来出现的NeRF改进模型进行了对比和评估。

NeRF全称为Neural Radiance Field，即神经辐射场，是一种用于3D重建的神经网络。训练时，NeRF接收一系列场景的

+ **NeRF**
	1. 优点：无需监督学习、适用场景多
	2. 缺点
	3. 网络结构
	4. 损失函数
	5. 数据集
 


