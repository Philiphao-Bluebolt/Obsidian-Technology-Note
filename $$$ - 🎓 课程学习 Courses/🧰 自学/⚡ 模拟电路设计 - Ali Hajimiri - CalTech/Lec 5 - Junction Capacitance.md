+ 链接 - [105N. PN Junction, Junction Capacitance, Doping Profile](https://www.youtube.com/watch?v=nSsaHG643xc&list=PLc7Gz02Znph-c2-ssFpRrzYwbzplXfXUT&index=5)
+ 关键词
	+ 结电容（Junction Capacitance）
	+ PN结（PN Junction）
	+ 耗尽层（Depletion Region）
	+ 反向偏置（Inverse Bias）
	+ 净电荷（Net Charge）
	+ 掺杂分布图（Doping Profile）

上节课最后简单介绍了PN结正向偏置时导电性增加的特性，这节课则讨论反向偏置时PN结表现的电容特性。

+ PN结的反向偏置（Inverse Bias）：外部电压源正极接N区，负极接P区，耗尽层变厚，只有较小的漂移电流Drift Current通过。

耗尽层（Depletion Region）横亘在P区与N区之间，起到了电介质（Dielectric）的作用，P区、N区与耗尽层的交界则相当于两个电容板，由此产生了结电容（Junction Capacitance）。这节课的内容，就是要计算出这个结电容的大小。

1. [[#平行板电容 Parallel Plate Capacitance]]
2. [[#耗尽层的净电荷及电场分布 Net Charge and Electric Field Distribution]]
3. [[#耗尽层的电势分布 Electric Potential Distribution]]
4. [[#结电容的表达式 Equation for Junction Capacitance]]

---
### 平行板电容 Parallel Plate Capacitance

平行板电容器的电容表达式为：
$$C=\frac{\varepsilon_s A}{d}$$（板间电介质电容率$\varepsilon_s$，极板面积$A$，板间距离$d$）

![[Pasted image 20241030152655.png]]

PN结的结电容（Junction Capacitance）等效为一个平行板电容器，因此它单位面积的电容量公式为：
$$C_{per A}=\frac{\varepsilon_s}{x_p+x_n}$$
其中，$x_p$、$x_n$分别指P区、N区一侧的耗尽层宽度，这也是需要求的未知参数。为了求出$x_p$、$x_n$的值，我们需要建立更多方程。

---
### 耗尽层的净电荷及电场分布 Net Charge and Electric Field Distribution

在开始研究PN结的电场电势分布以前，先简单说明其掺杂浓度的分布，即沿PN结水平方向，杂质原子的分布密度。反映掺杂浓度沿水平方向变化的图称为掺杂分布图（Doping Profile）

+ 掺杂突变结（Abrupt Junction）：杂质浓度在P区、N区之间突变。

![[Pasted image 20241030153004.png]]

在实际的半导体工业中，出于成本和性能考虑，不会生产Abrupt Junction。我们在下列计算中使用Abrupt Junction只是为了简化问题。

![[Pasted image 20241030153037.png]]

如图，在PN结中，只有耗尽层中存在内部电场，这是因为耗尽层靠近P区、N区的两侧分别存在不可移动的（Inmobilized）负离子和正离子，两者无法相互靠近，因此存在净电荷不为零的区域。在耗尽层以外的区域，即使存在大量载流子，它们均匀分布在带相反电荷的离子间，也使得区域净电荷为零。

假设P区的掺杂浓度为$N_A$，N区的掺杂浓度为$N_D$，杂质原子在各自区域中均匀分布，$N_A$单位为$\mathrm{mol/m^3}$。耗尽层中，靠近P区的杂质离子因空穴游离而带一单位净负电荷，净负电荷密度为$qN_A$，靠近N区的杂质离子因自由电子游离而带一单位净正电荷，净正电荷密度为$qN_D$。

由于整个PN结为电中性，因此耗尽层中正负电荷也是等量的，因此有了第一个方程：
$$qN_A Ax_p=qN_D Ax_n$$
由高斯定律积分可求得耗尽层中的电场分布，其中，电场强度的最大值$E_{max}$出现在P区与N区的交界处，即掺杂极性突变处。根据带电平行板之间的电场公式得到第二个方程：
$$E_{max}=\frac{qN_Dx_n}{\varepsilon_s}=\frac{qN_A x_p}{\varepsilon_s}$$
将$x_n+x_p$代入两个方程，可得：
$$E_{max}=\frac{q}{\varepsilon_s}\frac{N_AN_D}{N_A+N_D}(x_n+x_p)$$

至此，得到了耗尽层宽度$x_n+x_p$与电场最大值$E_{max}$的关系


---
### 耗尽层的电势分布 Electric Potential Distribution

对耗尽层的电场分布函数进行积分，由于电场分布函数是分段线性的（参照上图），很容易分别得到靠近P区与N区的电势差：
$$\psi_p=\frac{E_{max}x_p}{2}$$
$$\psi_n=\frac{E_{max}x_n}{2}$$
由于非耗尽层区域没有压降，这两个电势差的和就是耗尽层电压和外部电压的差。
$$\psi_p+\psi_n=\psi_o-V_D$$
代入上述式子，我们得到耗尽层总宽度$x_n+x_p$的表达式：
$$x_p+x_n=\sqrt{\frac{2\varepsilon_s}{q}(\psi_o-V_D)(\frac{1}{N_A}+\frac{1}{N_D})}$$
从式子中可以发现，掺杂浓度$N_D$、$N_A$越高，耗尽层总宽度越小；另外，掺杂浓度低的一侧总是占据耗尽层总宽度的绝大部分。


---
### 结电容的表达式 Equation for Junction Capacitance

最终，我们得到了单位面积结电容（Junction Capacitance）的表达式：
$$C_j(\mathrm{per A})=\sqrt{\frac{q\varepsilon_s}{2(\frac{1}{N_A}+\frac{1}{N_D})(\psi_o-V_D)}}$$
（元电荷量$q$，PN结材料的电容率$\varepsilon_s$，P区掺杂浓度$N_A$，N区掺杂浓度$N_D$）

可以看出，掺杂浓度$N_D$、$N_A$越高，单位面积结电容越大。

在实际生产中，若要生产尺寸较小的半导体器件，为了保证耗尽层尺寸与器件尺寸的比例不变，常需要提高掺杂浓度，造成单位面积结电容变大。不过，因为器件的截面积变小了，总电容也不会特别大。

最后，要注意表达式中的平方的由来是缘于对Abrupt Junction载流子浓度（分段常值函数）的两次积分（Intergral），因此，**掺杂分布特性不同的PN结会有不一样的结电容表达式**。



