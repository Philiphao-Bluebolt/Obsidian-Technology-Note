+ 链接 - [104N. PN Junction, Depletion Region, Diode Equation](https://www.youtube.com/watch?v=O_ntPMM0EQA&list=PLc7Gz02Znph-c2-ssFpRrzYwbzplXfXUT&index=4)
+ 关键词
	+ PN结（PN Junction）
	+ 耗尽层（Depletion Region）
	+ 能带弯曲（Band Bending）
	+ 偏置（Bias）
	+ 二极管方程（Diode Equation）

我们现在已经完全掌握一块半导体材料载流子密度（Carrier Density）、电导率（Conductivity）的求法，如果将一块P型半导体和一块N型半导体连接在一起组成PN结，又会发生什么呢？

 1. [[#PN结与耗尽层的形成 PN Junction and the Depletion Region]]
 2. [[#PN结的能带弯曲 Energy Band Bending of PN Junction]]
 3. [[#PN结外加偏置电压 Bias Voltage on PN Junction]]

---
### PN结与耗尽层的形成 PN Junction and the Depletion Region

在绝对零度$0\mathrm{K}$下，连接在一起的P型半导体和N型半导体仍旧是优良的绝缘体，因为没有外界热能激发，半导体中不存在任何的本征载流子和掺杂载流子。处于绝对零度的PN结，从P区到N区，导带下限能量$E_c$、价带上限能量$E_v$、费米能$E_f$都是一条平行的直线。

一但温度开始升高，情况就变得复杂起来。

在较低温度下，掺杂载流子首先被激发，P区激发出带正电的空穴，留下带负电的不可移动的掺杂元素离子，N区激发出带负电的自由电子，留下带正电的不可移动的掺杂元素离子。由于在P区中自由电子少，N区产生的自由电子会向P区扩散（Diffuse）；空穴同理。

扩散趋势使两者在PN区交界处浓度都很高，大量的自由电子和空穴在此处相互结合（Recombination），形成一个几乎不再有自由载流子的区域，称为耗尽层（Depletion Region）

![[Pasted image 20241030144243.png]]

在耗尽层中，P区部分只剩下带负电的离子，N区部分只剩下带正电的离子，因此会形成一个由N区指向P区的电场，阻碍两边的载流子继续向耗尽层扩散。同时，耗尽层中结合的自由电子和空穴也会分离并受电场力作用漂移到耗尽层外。因此，在热平衡（Thermal Equilibrium）下（无外界能量输入），耗尽层的宽度维持动态平衡。

耗尽层的平衡本质上是扩散电流（Diffusion Current）（自由电子和空穴扩散到PN区边界）和漂移电流（Drift Current）（受耗尽层电场力作用，自由电子回到N区，空穴回到P区）的平衡。


---
### PN结的能带弯曲 Energy Band Bending of PN Junction

P型和N型半导体结合后，整个PN结的能带图会有以下变化：

+ 费米能的统一（Align Fermi Energy）：P型半导体和N型半导体相连接，在建立热平衡的过程中，P区占多数的空穴和N区占多数的自由电子会向对面区域扩散。由于两者都遵循费米-狄拉克分布，热平衡建立后，整个PN结系统将会有一个恒定的费米能$E_f$；

+ 能带弯曲（Energy Band Bending）：耗尽层电场势能的存在使得自由电子向P区运动时能量会增加，空穴向N区运动时能量也增加，造成导带和价带在P区向上移动，在N区向下移动；

+ 能隙不变（Constant Band Gap）：由于能隙大小由本征材料决定，能隙的宽度（导带下限$E_c$与价带上限$E_v$能量差）在整个PN结中恒定。

![[Pasted image 20241030144857.png]]

另外，要注意能带图是反映自由电子（负载流子）的能量，因此同一条能带在P区（存在负离子）中的能量高于N区（存在正离子）。

从能量角度分析，耗尽层电压$\psi_o$使能带弯曲，由此建立起一个能量的势垒（Potential）$q\psi_o$，在P区占多数的空穴和在N区占多数的自由电子往对面的区域扩散时，都会受到阻碍。按费米-狄拉克分布（可用玻尔兹曼分布近似），只有少数大于$q\psi_o$的高能载流子能够跨越这个势垒，按照之前Lec2的推导，能通过的载流子比例正比于：
$$I_S=e^{-\frac{q\psi_o}{kT}}$$

后面会提到，这个 在二极管方程中称为饱和电流Saturation Current。如果外加一个从P区指向N区的正向电压，能够跨越耗尽层势垒的载流子就会呈指数级别增加。

---
### PN结外加偏置电压 Bias Voltage on PN Junction

+ PN结的正向偏置（Positive Bias）：外部电压源$V_D$的正极接P区，负极接N区。

正向偏置的PN结，由于外界电压$V_D$与耗尽层电压的方向$\psi_o$相反，耗尽层电压被削弱，势垒下降，有更多的载流子能穿越耗尽层，这部分多出来的载流子就形成流过PN结的电流。
$$J_n \propto (e^{-\frac{q(\psi_o-V_D)}{kT}}-e^{-\frac{q\psi_o}{kT}})\propto e^{-\frac{q\psi_o}{kT}}(e^{\frac{q V_D}{kT}}-1)$$

此即PN结的二极管方程（Diode Equation），它描述了二极管正向偏置时的伏安特性曲线
$$I_D=I_S(e^{\frac{q V_D}{kT}}-1)$$
定义热电压（Thermal Voltage）为，常温（$T=300\mathrm{K}$）下取值约为$26\mathrm{mV}$
$$V_T=\frac{kT}{q}$$
+ **二极管方程（Diode Equation）**
$$I_D=I_S(e^{\frac{V_D}{V_T}}-1)$$

