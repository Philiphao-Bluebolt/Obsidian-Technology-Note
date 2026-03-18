+ 链接 - [103N. Carrier Movement in Semiconductors, Drift and Diffusion](https://www.youtube.com/watch?v=bcohloKhWB0&list=PLc7Gz02Znph-c2-ssFpRrzYwbzplXfXUT&index=4)
+ 关键词
	+ 热运动（Thermal Motion）
	+ 漂移（Drift）
	+ 漂移速度（Drift Velocity）
	+ 迁移率（Mobility）
	+ 电流密度（Current Density）
	+ 微观欧姆定律（Microscopic Ohm’s Law）

这节课从微观层面介绍了载流子的两种运动，其中电场力引起的载流子定向漂移是半导体导电性以及电流的成因。课程小目标是从微观层面推导出半导体电导率$\sigma$的公式。

1. [[#载流子的热运动 Carrier Thermal Motion]]
2. [[#载流子在电场中的漂移运动 Carrier Drift in Electric Field]]
3. [[#电流 Electric Current]]
4. [[#微观欧姆定律 Microscopic Ohm’s Law]]
5. [[#电导率的微观表达式 Microscopic Equation for Conductivity]]

---
### 载流子的热运动 Carrier Thermal Motion

从经典力学角度切入，自由电子可以视为一种理想气体。按照气体动理论的解释，自由电子无规则热运动的动能与自由度$i$成正比，其自由度为$i=3$。
$$i\times\frac{kT}{2}=\frac{1}{2}m_*\overline{v^2}$$

（玻尔兹曼常数$k$，开尔文温度$T$，自由度为3，自由电子等效质量$m_*$）

电子的等效质量（Effective Mass）考虑晶体原子对自由电子运动的作用力，它大约是自由电子绝对质量的四分之一。
$$m_*=\frac{m_e}{4}$$
在常温$T=300\mathrm{K}$下，代入所有常数，可以计算得自由电子的热运动平均速率为：
$$\bar{v}=6\times10^5 \mathrm{m/s}$$
这是一个很高的速度，达到了光速的$0.1\%$，但如同花粉的布朗运动，这种热运动的方向是无规则的，因此对传导电能没有帮助。

---
### 载流子在电场中的漂移运动 Carrier Drift in Electric Field

在晶体空间中施加一个电场$E$，自由电子$q$会受到一个沿着电场负方向（由于电子带负电）的电场力。根据牛顿第二定律可以求出电子在下一次碰撞前达到的最大漂移速度。
$$F=-qE=\frac{dp}{dt}=\frac{m_*\Delta v}{\tau_c}$$
（电子仍使用等效质量$m_*$）

式中$\tau_c$指的是碰撞间平均自由时间（Mean Free Time between Collision），即自由电子在两次碰撞（碰撞会改变漂移运动方向）之间的时间。式中$\Delta v$即自由电子一段无碰撞直线运动期间在电场中加速达到的最大漂移速度（Max Drift Velocity）

![[Pasted image 20241030135650.png]]

可以想象，自由电子一段无碰撞直线运动期间的最小漂移速度是0（开始时），最大速度是$\Delta v$（结束时），场强$E$恒定时，沿漂移方向的分运动是匀加速运动。因此，考虑所有自由电子，它们任意时刻的平均漂移速度（Average Drift Velocity）$v_d$是$\Delta v$的一半，下式中的2由此而来。

$$v_d=-\frac{q\tau_c}{2m_*}\times E$$

上式说明，平均漂移速度$v_d$与电场强度$E$成正比。定义比例系数为$\mu_n$，称之为迁移率（Mobility）

$$\mu_n=\frac{q\tau_c}{2m_*}$$

经过粗略估算，单个电子平均漂移速度$v_d$数量级只有$10^{-2} \mathrm{m/s}$，相当于蜗牛的爬行速度，远小于其热运动平均速率$\bar{v}$，在电子的速度中是微不足道的分矢量（Component Vector），但从宏观角度上，由于单位导体材料体积内电子的数量是极大的（粗略计算至少是阿伏伽德罗常数数量级：$10^{23}$ ），这个微小分速度足以形成可观的电流。

+ 漂移速度的非线性饱和 （Nonlinear Saturation of Drift Velocity）：实际上，平均漂移速度$v_d$不可能随着电场强度$E$增大而一直增加，因为过高的漂移速度$v_d$会使电子的平均自由运动时间显著降低（朝电场方向撞在原子核上），因此电场强度$E$超过一定值，迁移率$\mu_n$会逐渐降低。最后，平均漂移速度$v_d$会达到一个饱和的最大值$v_{sat}$，现代集成电路的晶体管中，载流子多工作在这个速度下。

---
### 电流 Electric Current

电流的定义是，单位时间内流过导体横截面的电荷量：

$$I=\frac{dq}{dt}$$

而在单位时间$dt$内穿过某一横截面的电荷量$dq$，全部位于以平均漂移速度$v_d$扫过截面而形成的三维体积内，此三维体的体积为：（$A$为横截面积）
$$V=A\cdot v_d \cdot dt$$

![[Pasted image 20241030141427.png]]

对于半导体材料，代入上节课得出的载流子单位体积密度$n$和元电荷量$q$即求得$dq$：
$$dq=nV=-nqAv_d dt$$
所以，电流$I$即为：
$$I=\frac{dq}{dt}=\frac{-nqAv_ddt}{dt}=-nqAv_d$$
还能求出电流密度（Current Density）（单位横截面积的电流）：
$$J=\frac{I}{A}=-nqv_d=-nq\mu_nE$$
---
### 微观欧姆定律 Microscopic Ohm’s Law

在纯电阻电路（Pure Resistive Circuit）中，欧姆定律以电阻$R$（电导$G$）为系数联系起电压$V$和电流$I$，微观欧姆定律则以电阻率$\rho$（电导率$\sigma$）为系数联系起电场强度$E$和电流密度$J$，后者完全规避了横截面积$A$，长度$L$等宏观物理量。
$$\begin{cases}E=\rho J\\J=\sigma E\end{cases}\quad\leftarrow\quad \begin{cases} V=RI\\V=EL\\R=\rho\frac{L}{A}\\I=JA\end{cases}$$

---
### 电导率的微观表达式 Microscopic Equation for Conductivity

我们现在已经推导出下面这些公式，立即就能写出电导率$\sigma$的微观表达式。

+ 微观欧姆定律公式$J=\sigma E$
+ 载流子漂移速度和场强的关系式$v_d=-\mu_nE$
+ 微观电流密度表达式$J=-nqv_dE$

但是要注意，对于半导体而言，导电的载流子有两种：自由电子和空穴，前面的计算只考虑了自由电子漂移产生的电流，这里还要**考虑空穴漂移产生的电流**：
$$J_p=pq\mu_pE$$
总的电流密度$J$：
$$J=J_n+J_p=nq\mu_nE+pq\mu_pE$$
最后写出**电导率**$\sigma$**的微观表达式**：
$$\sigma=q(n\mu_n+p\mu_p)$$
通过前三节课的推导，我们成功地从微观层面推导出了电导率的公式，揭示了物质导电的微观成因，这有利于对半导体材料的学习。