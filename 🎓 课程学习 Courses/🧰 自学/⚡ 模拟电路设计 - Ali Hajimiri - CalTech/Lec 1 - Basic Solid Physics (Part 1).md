+ 链接 - [101N. Basic Solid-State Physics: Energy bands, Electrons and Holes](https://www.youtube.com/watch?v=403CnTftB4M&list=PLc7Gz02Znph-c2-ssFpRrzYwbzplXfXUT)
+ 关键词
	+ 电阻率（Resistivity）
	+ 氢原子能级（Energy Level）
	+ 能带理论（Energy Band Theory）
	+ 泡利不相容原理（Pauli Exclusive Principle）
	+ 载流子生成与结合（Carrier Generation and Combination）

第一节课，教授不厌其烦地用一整节大课的时间，从量子力学、化学的角度介绍半导体材料（Semiconductor Material）特性的微观成因。他的意思是，学习电路必须要从微观视觉（Microscopic View）切入才能充分理解。

1. [[#回顾：电阻率与电导率 Resistivity & Conductivity]]
2. [[#回顾：德布罗意波和氢原子轨道 De Broglie Wave, Hydrogen Orbital]]
3. [[#回顾：能级量子化 Quantized Energy Level]]
4. [[#半导体能带理论 Energy Band Theory]]
5. [[#载流子的产生 Generation of Carrier]]

---
### 回顾：电阻率与电导率 Resistivity & Conductivity

一块长为$L$，横截面积为$A$，电阻率为$\rho$的材料的电阻为
$$R=\rho\frac{L}{A}$$

![[Pasted image 20241002142334.png]]

电阻率$\rho$（Resistivity）单位为欧姆米（$\Omega \cdot m$），与形状无关，是物质的基本属性，它的倒数电导率$\sigma$（Conductivity）衡量物质导电性的强弱。
$$\sigma=\frac{1}{\rho}$$
导体-绝缘体的传统划定：

+ 超导体（Superconductor）：电阻率为$0$
+ 导体（Conductor）：电阻率小于$10^{-4}\Omega \cdot m$的物质，如铝（$10^{-8}\Omega \cdot m$）
+ 绝缘体（Insulator）：电阻率大于$10^{4}\Omega \cdot m$，如二氧化硅（$10^{14}\Omega \cdot m$）
+ 半导体（Semiconductor）：电阻率介于$10^{-4}\Omega \cdot m$和$10^{4}\Omega \cdot m$之间。

导电性的差异与物质的电子排布有关。


---
###  回顾：德布罗意波和氢原子轨道 De Broglie Wave, Hydrogen Orbital

德布罗意指出，一切实物粒子都有波粒二象性（Wave-Particle Duality），且其波长$\lambda$和动量$p$由普朗克常数$h$（Planck’s Constant）联系
$$\lambda=\frac{h}{p}$$
电子（Electron）作为一种微观的实物粒子，自然也满足以上定理。下面氢原子能级的计算中，采用玻尔行星模型（Bohr Model），即假设电子沿圆周轨道运动，这个模型有缺陷，但是可以解释能级的量子化。

结构最简单的氢原子，一个电子围绕一个质子（Proton）运动。根据玻尔模型，电子与质子间的库仑力提供向心力（Centrifugal Force）
$$F=\frac{e^2}{4\pi\varepsilon_0 r^2}=\frac{m_0v^2}{r}=\frac{p^2}{m_0 r}$$
+ 元电荷$e=1.6\times 10^{-19}C$
+ 真空介电常数$\varepsilon_0=8.85\times10^{-12}F/m$，
+ 电子质量$m_0=9.1\times10^{-31}kg$
+ 电子动量$p$
+ 电子轨道半径$r$

薛定谔指出，电子围绕原子核的运动必须满足驻波方程，即轨道周长是电子波长的整数倍
$$2\pi r=n\lambda=\frac{nh}{p}\quad(n\in N)$$
![[Pasted image 20241002151333.png]]

以上两个方程联立可以解出电子的轨道半径$r$和动量$p$，由于驻波方程整数系数$n$的限制，半径和动量取值都是离散（Discreted）的，解释了氢原子能级的量子化（Quantization）
$$r=\frac{n^2h^2\varepsilon_0}{\pi m_0e^2} $$$$\\p=\frac{m_0e^2}{2nh\varepsilon_0}$$

---
### 回顾：能级量子化 Quantized Energy Level

在绝对零度下，忽略外部能量，原子内部的能量归结为电子移动的动能（Kinetics Energy）和电子、质子电荷吸引作用（Electrotatic Attraction）引起的势能（Potential Energy）
$$E_{total}=E_{kinetics}+E_{potential}=\frac{p^2}{2m_0}-\frac{e^2}{4\pi \varepsilon_0r}=-\frac{p^2}{2m_0}=-\frac{13.6eV}{n^2}$$
稳定时，氢原子系统的总能量是量子化的负值，这意味着电子只能在某些离散的轨道上运动，一但外部能量输入使总能量大于0，电子就会逃逸。

![[Pasted image 20241002152619.png]]


---
### 半导体能带理论 Energy Band Theory 

半导体能带理论用量子力学解释固体材料中电子的行为，从而解释物质的导电性。

![[Pasted image 20241002160636.png]]

泡利不相容定理指出，两个全同费米子（Fermion）不能处在同一量子态（Quantum State），即必须具有不同的量子数。

电子是一种费米子，因此当多个原子形成一个分子时，其原子轨道（Atomic Orbital）重叠，同一能级的不同电子会发生能级简并（Energy Level Degeneracy），在同一能级附近形成一组能量不同（差异很小）的轨道，是为能带（Energy Band），不同能级的能带间的区域则成为禁带（Forbidden Band）或能隙（Band Gap）

碳的电子排布为$1s^22s^22p^2$，形成钻石时，其外层四个轨道$2s2p_x2p_y2p_z$发生杂化（Hybridisation），产生四个完全相同的$sp^3$杂化轨道，在能带理论中，则形成两条能带，阶带（Valence Band）和导带（Conduction Band）。碳原子外层的四个电子全部位于价带中。

由于价带完全被填满，导带完全没有电子，且两者间有难以跨越的能隙，因此在绝对零度下（无热量提供能量），钻石、纯硅等半导体是完全的绝缘体；而在非绝对零度下，由于外界热量可以为电子跨越能隙提供能量，它们的导电性随温度提高。这也是半导体材料负温度系数的成因。


---
### 载流子的产生 Generation of Carrier

实际环境中，温度不可能达到绝对零度，因此总有外界的分子动能为电子跨越能隙提供一定的能量。以绝对零度下完全绝缘的钻石为例，一但外界温度提供的能量足以使部分电子脱离价带，跨越能隙进入导带，价带就会产生空穴（Hole），导带就会有自由电子（Free Electron），空穴和自由电子都能移动，使得钻石导电。这就是载流子的生成（Generation）

这一过程从化学结构的层面上表现为部分电子脱离$sp^3$杂化轨道形成的$\sigma$碳碳单键，导致局部共价键断裂，产生局部带正电的空穴和带负电的自由电子。

载流子会生成，也会结合（Combination），在某一温度下，生成与结合的速率（Rate）相等时，就达到了一个平衡状态，载流子的数量维持动态平衡（Dynamic Balance）。

