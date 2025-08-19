这门课程是模拟电路设计的进阶版本，介绍了以下内容

+ [[#考点分析 Examination Keypoints]]
+ [[#电路分析基础 Basic Circuit Analysis]]
+ [[#Part 1 - 噪声分析 Noise Analysis]]
	+ [[#噪声相关计算 Calculation of Noise]]
	+ [[#元件噪声模型 Component Noise Model]]
	+ [[#等效输入噪声 Equivalent Input Noise]]
	+ [[#噪声因子 Noise Factor]]
	+ [[#噪声匹配 Noise Matching]]
+ [[#Part 2 - 带宽分析 Bandwidth Analysis]]
+ [[#Part 3 - 功率放大电路 Power Amplifier]]
	+ 
+ [[#Part 4 - 有源滤波电路 Active Filter]]
	+ [[#频率缩放与阻抗缩放 Frequency and Impedance Scaling]]
	+ [[#标准一阶及二阶滤波器 Standard First and Second Order Filter]]
	+ [[#双二阶滤波器 Biquadratic Filter]]
	+ [[#巴特沃斯滤波器 Butterworth Filter]]
	+ [[#切比雪夫滤波器 Chebyshev Filter]]
+ [[#Part 5 - 直流转换器 DC-DC Converter]]
	+ [[#设计指标与参数 Performances and Parameters]]
	+ [[#降压变换器 Buck Converter]]
	+ [[#升压变换器 Boost Converter]]
	+ [[#降压-升压变换器 Buck-Boost Converter]]
	+ [[#Ćuk降压-升压变换器 Ćuk Converter]]

---
## 考点分析 Examination Keypoints

近三年试卷的考点非常固定，四道大题完美覆盖了五个部分

+ 噪声分析与降噪：近三年都是共射放大器（第一大题）
	+ 画噪声等效电路
	+ 求输入等效噪声
	+ 变压器噪声匹配降低Noise Factor（第二大题）
+ 带宽分析：近三年都是场效应管
	+ 求中频增益、特征频率
	+ 画电路频率特性图
+ 功率放大电路：近三年都是Class A（第三大题或第四大题第一问）
+ 有源滤波电路：考Buttonworth或Biquadratic（第三大题或第四大题第一问）
+ 直流转换器：考Buck或Booth（第四大题第二问）

今年新增的两题可能会涉及

+ 切比雪夫滤波器
+ Class AB 或 Class D 功放

---
## 电路分析基础 Basic Circuit Analysis 

由于这门课程是模拟电路的进阶课程，电路分析、半导体元件等基础知识默认已经掌握，在讲课的过程中会不加解释直接使用，

### 二极管 Diode


### 三极管 BJT


### 场效应管 FET



---
## Part 1 - 噪声分析 Noise Analysis


### 噪声相关计算 Calculation of Noise



### 元件噪声模型 Component Noise Model

+ 二极管

+ 三极管

+ 场效应管

+ 运算放大器

### 等效输入噪声 Equivalent Input Noise



### 噪声因子 Noise Factor

噪声因子是输入与输出信噪比的比值


### 噪声匹配 Noise Matching

安装变压器对输入源进行电压以及阻抗变换，可以提高输出响应的信噪比$SNR$，利用求导即可以得到最大信噪比的对应变比$N$

![[Pasted image 20241203022923.png]]


---
## Part 2 - 带宽分析 Bandwidth Analysis


### 密勒效应 Miller Effect





### 计算特征频率 Calculation of Characteristic Frequency



---
## Part 3 - 功率放大电路 Power Amplifier


### AB型功放 Class AB Amplifier


### D型功放 Class D Amplifier

D型功放是一种数字开关功率放大电路，效率可达$90\%$以上，其基本工作原理是将输入正弦信号转化为PWM波，放大功率后再通过低通滤波器滤除高频分量，还原正弦信号。
![[Pasted image 20241203031434.png]]

在忽略晶体管压降的条件下，最大输出电压可达轨对轨，对应的输出功率如下
$$P_L=\frac{V_{CC}^2}{R_L}$$
D型功放的功耗主要来自晶体管的状态切换



### 散热片 Heat Sink

功率放大电路的耗散功率会转化为大量热能使设备温度升高，因此加装散热片是必要的。


---
## Part 4 - 有源滤波电路 Active Filter

有源滤波电路使用电阻、电容和运算放大器实现，是一种小体积，输入电阻大，输出电阻小的优良滤波器。

### 频率缩放与阻抗缩放 Frequency and Impedance Scaling

+ **频率缩放**：将一个截止频率为$1\mathrm{rad/s}$的标准滤波器的频率特性函数移动到任意截止频率$\alpha$处，等价为所有电抗元件的取值（电容$C$、电感$L$）除以$\alpha$

+ **阻抗缩放**：一个网络中所有阻抗（电阻$R$、电容$X_C$、电感$X_L$）同时乘以一个倍率$\beta$，网络的频率特性不变

### 标准一阶及二阶滤波器 Standard First and Second Order Filter

标准低阶滤波器是复杂滤波器的基本部件

| 滤波器  |                       传递函数                       |                           电路传递函数                           | 冗余增益 |                标准实现电路                |
| :--: | :----------------------------------------------: | :--------------------------------------------------------: | :--: | :----------------------------------: |
| 一阶低通 |              $$H(s)=\frac{1}{s+1}$$              |             $$H(j\omega)=\frac{1}{1+j\omega}$$             |      | ![[Pasted image 20241202235326.png]] |
| 一阶高通 |              $$H(s)=\frac{s}{s+1}$$              |         $$H(j\omega)=\frac{j\omega }{1+j\omega}$$          |      | ![[Pasted image 20241203000059.png]] |
| 二阶低通 |      $$H(s)=\frac{1}{s^2+\frac{1}{Q}s+1}$$       |     $$H(j\omega)=\frac{A}{-\omega^2+j\omega(3-A)+1}$$      | $A$  | ![[Pasted image 20241203000120.png]] |
| 二阶高通 |     $$H(s)=\frac{s^2}{s^2+\frac{1}{Q}s+1}$$      | $$H(j\omega)=\frac{-\omega^2A}{-\omega^2+j\omega(3-A)+1}$$ | $A$  | ![[Pasted image 20241203000127.png]] |
| 二阶带通 | $$H(s)=\frac{\frac{1}{Q}s}{s^2+\frac{1}{Q}s+1}$$ |                                                            |      |             （由双二阶滤波器实现）              |
| 二阶带阻 |    $$H(s)=\frac{s^2+1}{s^2+\frac{1}{Q}s+1}$$     |                                                            |      |           （由二阶高通和低通结果相加实现）           |

### 双二阶滤波器 Biquadratic Filter

双二阶滤波器可以同时输出二阶高通、带通、低通的结果，其传递函数的特征式由电阻$(2Q-1)$调整。注意输出需要串联一个比例运算电路消除冗余增益


![[Pasted image 20241110144700.png]]


### 巴特沃斯滤波器 Butterworth Filter

巴特沃斯滤波器是一种频率响应平坦的低通滤波器，其单位截止频率的标准形式由以下的式子描述，其中$n$是滤波器的阶数。阶数越高，巴特沃斯滤波器在截止频率后段的幅值衰减越快
$$|H(j\omega)|=\frac{1}{\sqrt{1+\omega^{2n}}}$$
设计巴特沃斯滤波器的步骤：

1. 根据期望的衰减速度选择最小所需阶数
2. 查巴特沃斯滤波器表，找出对应阶数的传递函数
3. 用一阶、二阶滤波器串联实现

![[Pasted image 20241203002147.png]]

### 切比雪夫滤波器 Chebyshev Filter





---
## Part 5 - 直流转换器 DC-DC Converter

直流转换器是适用于直流电的变压器，传统设计一般基于线性稳压器架构，现在常用的设计则使用数字化的开关电源式（Switching-mode）架构，这种架构的输出电压不受负载影响且效率可达$90\%$

开关电源式直流转换器有四种常用构型，分别是Buck、Boost、Buck-Boost、Cuk，它们的分析设计过程有以下共同点：

+ **理想化无损耗**：二极管正向短路反向开路，除电源和负载以外的元件忽略功耗
+ **LC积分惯性不变向**：由于开关频率高，电容和电感取值大，电容电压$v_C$和电感电流$i_L$都维持方向不变
+ **LC零平均功耗**：由于电容和电感是无源器件，而$v_C$和$i_L$在一个周期内的平均不为零，因此$i_C$和$v_L$一个周期内的平均必为0
$$V_CI_C=0\quad\quad V_L I_L=0$$
+ **输入输出电压视为恒定**：除非是做输出纹波分析

分析过程中会用到平均值（大写$V,I$）和瞬时值（小写$v,i$）

### 设计指标与参数 Performances and Parameters

开关电源式直流转换器的设计需要满足以下要求

+ 给定的恒定输入电压$V_S$
+ 给定的负载电阻$R$
+ 所需的输出电压$V_o$
+ 保证输出电压最大波动比$\Delta V_o/{V_o}$低于设定值
+ 保证电感器电流$i_L$方向不变（即$I_\min>0$）

设计过程中需要确定的参数如下，开关频率$f$可能已知

+ 开关占空比$D$：决定输出电压$V_o$与输入电压$V_S$的倍乘关系
+ 开关频率$f$：影响电感和电容的取值范围
+ 电感取值$L$：决定电感电流$i_L$能否维持方向不变
+ 电容取值$C$：决定输出电压的波动幅值$\Delta V_o$

| Type       | Input-output            | Inductor                         | Capacitor                                        |
| :--------- | :---------------------- | :------------------------------- | :----------------------------------------------- |
| Buck       | $V_o=DV_S$              | $L_{\min}=\frac{(1-D)R}{2f}$     | $C=\frac{(1-D)}{8Lf^2\frac{\Delta V_o}{V_o}}$    |
| Boost      | $V_o=\frac{V_S}{1-D}$   | $L_{\min}=\frac{D(1-D)^2R}{2f}$  | $C=\frac{D}{Rf\frac{\Delta V_o}{V_o}}$           |
| Buck-Boost | $V_o=-\frac{DV_S}{1-D}$ | $L_{\min}=\frac{(1-D)^2R}{2f}$   | $C=\frac{D}{Rf\frac{\Delta V_o}{V_o}}$           |
| Cuk        | $V_o=-\frac{DV_S}{1-D}$ | $L_{1\min}=\frac{(1-D)^2R}{2Df}$ | $C_1=\frac{-D}{Rf\frac{\Delta V_{C1}}{V_o}}$     |
|            |                         | $L_{2\min}=\frac{(1-D)R}{2f}$    | $C_2=\frac{D}{8f^2L_2\frac{\Delta V_{C2}}{V_s}}$ |

### 降压变换器 Buck Converter

![[Pasted image 20241202171719.png]]

+ 求电感$L$电压电流关系（$\Delta i_{L\mathrm{on}}=-\Delta i_{L\mathrm{off}}$）

$$\quad v_L=v_s-v_o=L\frac{di_L}{dt}=L\frac{\Delta i_{L\mathrm{on}}}{DT}$$
$$v_L=-v_o=L\frac{di_L}{dt}=L\frac{\Delta i_{L\mathrm{off}}}{(1-D)T}$$

+ 求输入输出倍乘比$V_o/V_s$：利用电感周期平均电压为0的特性，也可以联立电感电压电流关系式

$$\begin{align}V_L=\frac{1}{T}\int_0^Tv_Ldt=\frac{1}{T}[\int_0^{DT}(v_s-v_o)dt+\int_{DT}^{T}-v_odt]&=0\\\frac{1}{T}[DT(v_s-v_o)-Tv_o+DTv_o]&=0\\v_o&=Dv_s\end{align}$$

+ 求电感$L$取值：必须使$I_\min>0$，利用电感上升电流的关系式与电容平均电流为0的特性

$$\begin{cases}I_L=I_C+I_o=I_o\\\Delta i_{L\mathrm{on}}=\frac{V_o(1-D)T}{L}\end{cases}\quad\to\quad I_\min=I_L-\frac{\Delta i_{L\mathrm{on}}}{2}=\frac{V_o}{R}-\frac{V_o(1-D)T}{2L}>0$$
$$L>L_\min=\frac{R(1-D)}{2f}$$

+ 求电容$C$取值：必须使$\Delta V_o/{V_o}$小于设定值，波动幅值$\Delta V_o$可由电容电荷量变化$\Delta Q$估算

$$\begin{cases}\Delta Q=C\Delta V_o\\\color{blue}\Delta Q=\frac{1}{2}\times\frac{T}{2}\times\frac{\Delta i_{L\mathrm{on}}}{2}\end{cases}\quad\to\quad \Delta V_o=\frac{(1-D)V_oT^2}{8CL}$$
$$C>\frac{(1-D)}{8Lf^2(\frac{\Delta V_o}{V_o})_\max}$$
### 升压变换器 Boost Converter

![[Pasted image 20241202171737.png]]

+ 求电感$L$电压电流关系（$\Delta i_{L\mathrm{on}}=-\Delta i_{L\mathrm{off}}$）：与Buck求法相同

$$\quad v_L=v_s=L\frac{di_L}{dt}=L\frac{\Delta i_{L\mathrm{on}}}{DT}$$
$$v_L=v_s-v_o=L\frac{di_L}{dt}=L\frac{\Delta i_{L\mathrm{off}}}{(1-D)T}$$

+ 求输入输出倍乘比$V_o/V_s$：与Buck求法相同

$$\begin{align}V_L=\frac{1}{T}\int_0^Tv_Ldt=\frac{1}{T}[\int_0^{DT}v_sdt+\int_{DT}^{T}(v_s-v_o)dt]&=0\\\frac{1}{T}[DTv_s+T(1-D)(v_s-v_o)]&=0\\v_o&=\frac{v_s}{1-D}\end{align}$$

+ 求电感$L$取值：与Buck求法不同，因为$i_L=i_C+i_o$不在整个周期里成立，这里转而利用理想变换器输入输出功率守恒的特性用$V_s$表示$I_L$ 

$$\begin{cases}V_sI_L=\frac{V_o^2}{R}\\\Delta i_{L\mathrm{on}}=\frac{DTV_s}{L}\end{cases}\quad\to\quad I_\min=I_L-\frac{\Delta i_{L\mathrm{on}}}{2}=\frac{V_s}{(1-D)^2R}-\frac{DTV_s}{2L}>0$$
$$L>L_\min=\frac{D(1-D)^2R}{2f}$$

+ 求电容$C$取值：与Buck求法相同但$\Delta Q$算法稍有不同，这里电容放电电流可近似为常值

$$\begin{cases}\Delta Q=C\Delta V_o\\\color{blue}\Delta Q=\frac{V_o}{R}DT\end{cases}\quad\to\quad \Delta V_o=\frac{V_oDT}{CR}$$
$$C>\frac{D}{Rf(\frac{\Delta V_o}{V_o})_\max}$$

### 降压-升压变换器 Buck-Boost Converter

![[Pasted image 20241202171754.png]]

+ 求电感$L$电压电流关系（$\Delta i_{L\mathrm{on}}=-\Delta i_{L\mathrm{off}}$）：与Buck求法相同

$$\quad v_L=v_s=L\frac{di_L}{dt}=L\frac{\Delta i_{L\mathrm{on}}}{DT}$$
$$v_L=v_o=L\frac{di_L}{dt}=L\frac{\Delta i_{L\mathrm{off}}}{(1-D)T}$$

+ 求输入输出倍乘比$V_o/V_s$：与Buck求法相同

$$\begin{align}V_L=\frac{1}{T}\int_0^Tv_Ldt=\frac{1}{T}[\int_0^{DT}v_sdt+\int_{DT}^{T}v_odt]&=0\\\frac{1}{T}[DTv_s+T(1-D)v_o]&=0\\v_o&=-\frac{Dv_s}{1-D}\end{align}$$

+ 求电感$L$取值：与Booth求法利用功率守恒类似，但需要一个额外条件$I_s=DI_L$，因为每个周期只有开关开启时才有$i_s=i_L$，其他时候$i_s=0$

$$\begin{cases}V_sI_s=\frac{V_o^2}{R}\\I_s=DI_L\\\Delta i_{L\mathrm{on}}=\frac{DTV_s}{L}\end{cases}\quad\to\quad I_\min=I_L-\frac{\Delta i_{L\mathrm{on}}}{2}=\frac{DV_s}{(1-D)^2R}-\frac{DTV_s}{2L}>0$$
$$L>L_\min=\frac{(1-D)^2R}{2f}$$
+ 求电容$C$取值：与Booth完全相同

$$\begin{cases}\Delta Q=C\Delta V_o\\\color{blue}\Delta Q=\frac{V_o}{R}DT\end{cases}\quad\to\quad \Delta V_o=\frac{V_oDT}{CR}$$
$$C>\frac{D}{Rf(\frac{\Delta V_o}{V_o})_\max}$$

### Ćuk降压-升压变换器 Ćuk Converter


