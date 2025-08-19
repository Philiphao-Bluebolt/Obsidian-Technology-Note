
---


![[64341 Assignment 1 _ 2024.pdf]]

---
## Queation

For the AC equivalent circuit of a common-emitter BJT amplifier shown in the figure, assume that $V_{CC} = 10 V$, $V_{BE} = 0.7 V$, $R_S =5 k\Omega$, $R_B=100k\Omega$, $R_L = 1 k\Omega$, $C_{b'e} = 2 pF$, $C_{c b'} = 1 pF$, and $C_L = 1 pF$. Assume bias current $I_B = 25 \mu A$, Boltzmann's constant $k = 1.38 \times 10^{-23} J/K$, $q =1.6 \times10^{-19} C$, $T = 300 K$, $V_T = 26 mV$, $\beta = 100$, $r_{bb'} = 100 Ω$, and ignore $𝑟_𝑜$ . Assuming the equivalent noise bandwidth is $100 kHz$, and neglecting the flicker noise and all capacitive effect.

(Note: For the BJT biased on the forward active region: $r_\pi = \frac{V_T}{I_B}$ , $g_m=\frac{I_C}{V_T}$)

+ (a) Calculate the total equivalent input RMS noise voltage and current by looking into node $a$

+ (b) Calculate the total equivalent input RMS noise voltage and current by looking into node $b$

+ (c) Discuss if a transformer (with turn ratio $1:N$) can be incorporated into point $b$ to minimize the total input referred noise? If yes, what is the $N$ to be?

![[Pasted image 20240909162114.png]]

---
## Solution

Remember to neglect all the capacitance and flicker noise (and burst noise)
![[Pasted image 20240909163126.png]]
### (a)

When looking into point a, all of the circuit's noises including the noise of the source resistance $R_S$ should be taken into account.

First we calculate the **equvalent noise voltage**. Short-circuit the input of both the original noise model and equivalent noise model.

![[Pasted image 20240909170542.png]]

The effect of equivalent input noise source $\overline{v^2_i}$ on the output voltage is the same as the the original noises, so we have
$$(g_mR_L\frac{(r_{bb'}+r_\pi)//R_B}{R_S+(r_{bb'}+r_\pi)//R_B}\frac{r_\pi}{r_\pi+r_{bb'}})^2\overline{v_i^2}=R_L^2\{\overline{i_c^2}+\overline{i_L^2}+g_m^2[(R_S//R_B+r_{bb'})//r_\pi]^2 \overline{i_b^2}+(\frac{r_\pi g_m}{R_S//R_B+r_{bb'}+r_\pi})^2\overline{v_b^2} +\{g_m[(R_S//R_B)//(r_{bb'}+r_\pi)]\frac{r_\pi}{r_{bb'+r_\pi}}\}^2 \overline{i_B^2}+(g_m\frac{(r_{bb'}+r_\pi)//R_B}{R_S+(r_{bb'}+r_\pi)//R_B}\frac{r_\pi}{r_\pi+r_{bb'}})^2\overline{v_S^2}\}$$

The original noises are described by the following equations.
$$\overline{v^2_S}=4kTR_S=8.28\times10^{-17}\quad V^2/Hz$$
$$\overline{i_B^2}=\frac{4kT}{R_B}=1.656\times10^{-25}\quad  A^2/Hz$$
$$\overline{v^2_b}=4kTr_{bb'}=1.656\times10^{-18}\quad V^2/Hz$$
$$\overline{i_b^2}=2qI_B=8\times10^{-24}\quad A^2/Hz$$
$$\overline{i_c^2}=2qI_C=8\times10^{-22}\quad A^2/Hz$$
$$\overline{i_L^2}=4kTR_L=1.656\times10^{-17} \quad A^2/Hz$$

Now calculate two unknown parameters $r_\pi$ and $g_m$ in the equation.
$$g_m=\frac{I_C}{V  _T}=\frac{\beta I_B}{V  _T}=\frac{100 \times 25\mu A}{26mV}=96mS$$
$$r_\pi=\frac{V_T}{I_B}=\frac{26mV}{25\mu A}=1040\Omega$$
Now subtitute all the parameters into the equation and ... we will get
$$\overline{v^2_i}=6.413\times10^{-14} \quad V^2/Hz$$
$$V_{irms}=\sqrt{\overline{v^2_i}\Delta f}=8.01\times10^{-5}V=80.1\mu V$$

Then is the **equvalent noise current**, this time we open-circuit both inputs.
![[Pasted image 20240909174755.png]]

Similarly, the equivalent noise current should represent all the noises. Notice that $\overline{v_S^2}$ and $R_S$ have no effect on the noise circuit.
$$[g_mR_L(R_B//(r_{bb'}+r_\pi))]^2\overline{i^2_i}=R_L^2\{\overline{i_c^2}+\overline{i_L^2}+[g_m(R_B//(r_{bb'}+r_\pi))]^2\overline{i^2_B}+(g_m\frac{r_\pi}{R_B+r_{bb'}+r_\pi})^2\overline{v^2_b}+[g_m(r_\pi//(r_{bb'+R_B}))]^2\overline{i^2_b}\}$$

Substitute the parameters to get the final result.
$$\overline{i_i^2}=1.421\times10^{-21}\quad A^2/Hz$$
$$I_{irms}=\sqrt{\overline{i^2_i}\Delta f}=1.192\times10^{-8}A=11.92nA$$

### (b)

When looking into point B, the source resistance $R_S$ and its thermal noise $\overline{v^2_S}$ will be excluded from the equivalent noise model, making the model ironically simpler.
![[Pasted image 20240909202437.png]]

The equivalent noise voltage can be calculated by the following equation. Interestingly, $\overline{i_B^2}$ have no effect on the output owing to the short circuit at the input. 
$$(g_mR_L\frac{r_\pi}{r_{bb'}+r_\pi})^2\overline{v^2_i}=R_L^2\{\overline{i^2_c}+\overline{i^2_L}+[g_m(r_\pi//r_{bb'})]^2\overline{i^2_b}+(g_m\frac{r_\pi}{r_{bb'}+r_\pi})^2\overline{v^2_b}\}$$
Then we get
$$\overline{v^2_i}=2.161\times10^{-15} \quad V^2/Hz$$
$$V_{irms}=\sqrt{\overline{v^2_i}\Delta f}=1.47\times10^{-5} V=14.7\mu V$$
![[Pasted image 20240909205335.png]]

Then is the equivalent noise current. Interestingly, it is exactly the same as the equivalent noise current when looking into point $a$.
$$[g_mR_L(R_B//(r_{bb'}+r_\pi))]^2\overline{i^2_i}=R_L^2\{\overline{i_c^2}+\overline{i_L^2}+[g_m(R_B//(r_{bb'}+r_\pi))]^2\overline{i^2_B}+(g_m\frac{r_\pi}{R_B+r_{bb'}+r_\pi})^2\overline{v^2_b}+[g_m(r_\pi//(r_{bb'+R_B}))]^2\overline{i^2_b}\}$$

Substitute the parameters to get the final result.
$$\overline{i_i^2}=1.421\times10^{-21}\quad A^2/Hz$$
$$I_{irms}=\sqrt{\overline{i^2_i}\Delta f}=1.192\times10^{-8}A=11.92nA$$

## (c)

Assume that we installed a $1:N$ transformer into point $b$, the equivalent circuit with amplifier noise looking into $b$ is shown in the graph.

![[Pasted image 20240909224115.png]]

Since the signal source resistance thermal noise is amplified, the noise power can not be directly reduced by the transformer. However, the transformer can reduce output SNR to a minimum value.

The $N$ can be calculated by the equation
$$N=\sqrt{\frac{v_i/i_i}{R_S}}=0.4966$$


---
## Final Result

+ (a) $V_{irms}=80.1\mu V$, $I_{irms}=11.92nA$
+ (b) $V_{irms}=14.7\mu V$, $I_{irms}=11.92nA$
+ (c) $N=0.4966$

