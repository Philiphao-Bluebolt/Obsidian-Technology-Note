
+ **June** - [6](#^f25d12) - 
+ **May** - [28](#^36bea9) - [27](#^ec614e) 






---

> **[3DGS.zip: A survey on 3D Gaussian Splatting Compression Method](https://arxiv.org/pdf/2407.09510)** ^f25d12

这是一篇针对3DGS方法的综述，



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
 


