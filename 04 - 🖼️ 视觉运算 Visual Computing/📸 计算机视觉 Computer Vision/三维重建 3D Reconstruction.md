
+ [评估指标 Evaluation Criteria](#评估指标%20Evaluation%20Criteria)
	+ [峰值信噪比 PSNR](#峰值信噪比%20PSNR)
	+ [结构性相似指标 SSIM](#结构性相似指标%20SSIM)
	+ [学习感知图像块相似度 LPIPS](#学习感知图像块相似度%20LPIPS)


---
## 




---
## 评估指标 Evaluation Criteria

三维重建论文中的实验分析部分经常能看到三个指标：PSNR、SSIM、LPIPS，前两种指标基于确定性公式，LPIPS则基于机器学习。三种指标都是计算机视觉领域的常用指标，用于衡量两幅图像之间的差异。

### 峰值信噪比 PSNR

+ **参考** - [PSNR](https://en.wikipedia.org/wiki/Peak_signal-to-noise_ratio)

PSNR（Peak Signal-to-Noise Ratio）是衡量输出图像与参考图像（Ground True）像素级差异的指标，它本质上依次经过归一化、倒数化、对数化的像素均方误差（$MAX$表示图像格式的最大像素值）
$$\mathrm{PSNR}(I_1,I_2)=10\lg(\frac{MAX^2}{MSE})=10\lg(\frac{MAX^2}{\frac{1}{HW}\sum_{i=1}^W\sum_{j=1}^H[I_1(i,j)-I_2(i,j)]^2})$$
+ **单位** - $\mathrm{dB}$
+ **取值范围** - $\mathrm{PSNR}\in[0,+\infty)$
+ **评判标准** - 取值越大像素差异越小

这是一个与空间分布无关的指标，仅考虑两幅图像之间对应像素的差异，不考虑连续变化的材质、结构等高频特征以及亮度偏差，因此与人类视觉判断的差异较大，不能代表人类的感知。


### 结构性相似指标 SSIM

+ **参考** - [SSIM](https://en.wikipedia.org/wiki/Structural_similarity_index_measure)

SSIM（Structural Similarity Index Measure）是一个以图像块为单位的评估指标，其计算公式包含了图像块内像素值的均值和标准差，其中$\mu_1,\mu_2$是分别两幅图像的像素均值，$\sigma_1,\sigma_2$是标准差，$\sigma_{12}$是协方差，$c_1,c_2$是为了避免出现零值而任选的小常量
$$\mathrm{SSIM}(I_1,I_2)=\frac{(2\mu_1\mu_2+c_1)(2\sigma_{12}+c_2)}{(\mu_1^2+\mu^2_2+c_1)(\sigma_1^2+\sigma^2_2+c_2)}$$
+ **取值范围** - 
+ **评判标准** - 越接近1越相似

这个指标考虑了两幅图像之间由亮度和对比度变化引起的差异以及低频结构差异，与PSNR相比更加关注高频特征。

+ **补充**：完整版公式中，相乘的三项分别代表对应两个图像块亮度、对比度、结构的差异，上述简化版本的乘项幂数取一，合并了后两项
$$\begin{align}\mathrm{SSIM}(I_1,I_2)&=l(I_1,I_2)^\alpha \cdot c(I_1,I_2)^\beta \cdot s(I_1,I_2)^\gamma\\&=(\frac{2\mu_1\mu_2+c_1}{\mu^2_1+\mu_2^2+c_1})^\alpha\cdot(\frac{2\sigma_1\sigma_2+c_2}{\sigma_1^2+\sigma_2^2+c_2})^\beta\cdot(\frac{\sigma_{12}+c_3}{\sigma_1\sigma_2+c_3})^\gamma\end{align}$$

### 学习感知图像块相似度 LPIPS

+ **参考** - 

LPIPS（Learned Perceptual Image Patch Similarity）是一种基于预训练视觉神经网络的图像相似度指标，网络模型一般选用AlexNet、SqueezeNet、VGG。Python的`lpips`库提供了可用的模型。

+ **评判标准** - 越接近0越相似

由于这几种网络的训练原理是基于人类标注的图像数据的有监督学习，LPIPS的评判与人类真实的视觉感知最为相似