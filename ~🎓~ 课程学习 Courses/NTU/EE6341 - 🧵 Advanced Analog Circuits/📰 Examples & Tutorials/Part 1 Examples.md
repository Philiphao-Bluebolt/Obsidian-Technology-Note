
+ [[#Introduction to Circuit Noise]]
	+ [[#1-1 Output noise calculation of a simple RC network]]
	+ [[#1-2 Calculate Equivalent noise bandwidth from a bode plot]]
	+ [[#1-3 Calculate the RMS thermal noise of a resistor]]
	+ [[#1-4 Calculate the RMS excess noise of a resistor]]
+ [[#Noise model of semiconductor components]]
	+ [[#1-5 Noise analysis for a BJT amplifier circuit]]
	+ [[#1-6 Calculate BJT Equivalent Input Noise]]
	+ [[#1-7 Calculate FET Equivalent Input Noise]]
	+ [[#1-8 Calculate Equivalent Input Noise Voltage of a Op Amp Amplifier]]
+ [[#Noise Analysis]]




---
## Introduction to Circuit Noise

#### 1-1  Output noise calculation of a simple RC network

For the given RC network, find the network function and denote the output noise PSD by the input noise PSD $\overline{v_i^2}$
![[Pasted image 20240830160604.png]]

First, we can easily write down the network function using the Kirchhoff Current Law (The voltage here are phasors)
$$\begin{align}\frac{V_i-V_o}{R}&=V_oj\omega C\\ H(j\omega)=\frac{V_o}{V_i}&=\frac{1}{1+j\omega RC} \end{align}$$
Then we derive the intensity part of the network function
$$|H(j\omega)|=|\frac{1}{1+j\omega RC}|=\sqrt{(\frac{1}{1+\omega^2R^2C^2})^2+(\frac{\omega RC}{1+\omega^2R^2C^2})^2}=\frac{1}{\sqrt{1+\omega^2R^2C^2}}$$
Then we get the output noise PSD using the square of network function intensity
$$\overline{v_o^2}=|H(j\omega)|^2\overline{v_i^2}=\frac{\overline{v_i^2}}{1+\omega^2R^2C^2}$$
At last, change the variable to frequency $f$ and use harmonic frequency $f_0=1/2\pi RC$ in the equation for simplicity.
$$\overline{v_o^2}=\frac{\overline{v_i^2}}{1+(f/f_0)^2}$$

#### 1-2  Calculate Equivalent noise bandwidth from a bode plot

Find the equivalent noise bandwidth $\Delta f$ for an amplifier whose frequency characteristics is described by the given bode plot

![[Pasted image 20240830171704.png]]

First, we must write down the transfer function of the given bode plot.

+ Low pass network
+ First-order as the decay slope is $-20dB/dec$
+ Mid frequency gain is $A_0$
+ Cutoff frequency is $f_o$

The transfer function is reconstructable with the conclusions above. We only need the intensity part of it.
$$|H(j\omega)|=\frac{A_0}{\sqrt{1+(f/f_0)^2}}$$
Now calculate the equivalent noise bandwidth. Notice that it uses the **square of intensity** in the equation because we're more interested in the power of noise
$$\begin{align}\Delta f A_0^2&=\int_0^\infty |H(jf)|^2df \\
\Delta f&=\int_0^\infty \frac{1}{1+(f/f_o)^2}df\\
&=\frac{\pi f_0}{2}\end{align}$$
The result indicates that the equivalent noise bandwidth $\Delta f$ is related to the -3dB cutoff frequency $f_0$ and the order of the network.


#### 1-3  Calculate the RMS thermal noise of a resistor

Calculate the RMS noise voltage of a $1k\Omega$ resistor at room temperature ($T = 300 K$), the equivalent noise bandwidth is $1MHz$. ($k=1.38\times 10^{-23} J/K$)
![[Pasted image 20240830232332.png]]
First we calculate the PSD of the thermal noise 
$$\overline{v^2}=4kRT=1.7\times 10^{-17} V^2/Hz$$
Then we can directly calculate the RMS noise using the equivalent noise bandwidth
$$V_{rms}=\sqrt{\overline{v^2}\Delta f}=4.12\times 10^{-6} V$$


#### 1-4  Calculate the RMS excess and thermal noise of a resistor

Given $R=10k\Omega$ with $NI = 10^{-6} V/V$. The DC voltage across it is $10 V$. Determine the total rms noise between $10 Hz$ and $10 kHz$ and plot the noise voltage PSD of the resistor.
![[Pasted image 20240831134256.png]]

From the introduction of Excess noise, we know that $NI$ is a parameter describing the RMS of excess noise over a decade of frequency divided by the DC voltage parameter.
$$NI=\frac{V_{rms-decade}}{V_D}=\frac{\sqrt{\int_{f_0}^{10f_0}\frac{m^2V_D^2}{f}}}{V_D}=m\sqrt{\ln10}$$
Then we can calculate the excess noise PSD using $NI$
$$\overline{v^2_e}=\frac{m^2 V_D^2}{f}=\frac{(NI)^2V_D^2}{f\ln10}$$
The sum of the thermal noise and excess noise can be obtained using the sum of square law.
$$\overline{v^2}=\overline{v^2_e}+\overline{v^2_t}=\frac{(NI)^2V_D^2}{f\ln10}+4kRT=\frac{4.3\times 10^{-11}}{f}+1.7\times 10^{-16} \quad V^2/Hz$$
The plot of the PSD:

![[Pasted image 20240831141051.png]]

Finally, the noise between two given frequency is calculated by a integral
$$V_{rms}=\sqrt{\int_{f_1}^{f_2}\frac{(NI)^2V_D^2}{f\ln10}+4kRT\quad df}=\sqrt{\frac{(NI)^2V_D^2}{\ln10}\int_{f_1}^{f_2}\frac{1}{f}df+4kRT\int_{f_1}^{f_2}d}=17.3\mu V$$


---
## Noise model of semiconductor components

#### 1-5  Noise analysis for a BJT amplifier circuit

The following circuit is a simple BJT amplifier with a input source and a load. Calculate the RMS of the total output noise. ($I_C=100\mu A$, $\beta=100$, $r_b =200\Omega$, $R_S=500\Omega$, $C_\pi=10pF$, $R_L=5k\Omega$, $4kT = 1.66 \times10^{-20}J$, $q=1.6\times10^{-19} C$)

+ Thermal Voltage $V_T=26mV$
+ Neglect flicker noise and burst noise for simplicity

![[Pasted image 20240831145255.png]]

First, we must replace the BJT with its hybrid-pi model and build up the noise model for the whole circuit. 

The circuit has five noise sources. Except for the three noises produced by the BJT, the inner resistance $R_S$ of the power source and the load resistance $R_L$ each produce one noise.

![[Pasted image 20240831153739.png]]

Remember that there exists a **superposition law** which applies to every linear system, meaning that the total output noise response of the circuit can be view as the sum of the five noise sources. Then we can calculate the response of each noise independently.

First we calculate network function for each noise.
$$v_{o1}=\frac{r_\pi\parallel C_\pi}{R_S+r_b+r_\pi \parallel C_\pi}g_m R_Lv_S$$
$$v_{o2}=\frac{r_\pi\parallel C_\pi}{R_S+r_b+r_\pi\parallel C_\pi}g_m R_Lv_b$$
$$v_{o3}=\frac{(R_S+r_b)(r_\pi \parallel C_\pi)}{R_S+r_b+r_\pi\parallel C_\pi}g_mR_Li_b$$
$$v_{o4}=R_L i_c$$
$$v_{o5}=R_Li_L$$
Then we write the expression of PSD for each noise. Ignore flicker noise and burst noise of base current.
$$\overline{v_S^2}=4kTR_S$$
$$\overline{v_b^2}=4kTr_b$$
$$\overline{i^2_b}=2qI_B+k_1\frac{I_B^a}{f}+k_2\frac{I_B^b}{1+(f/f_c)^2}\approx2qI_B$$
$$\overline{i_c^2}=2qI_C$$
$$\overline{i_L^2}=\frac{4kT}{R_L}$$
Then we use the sum of square law to combine all the PSD of noise into one. The result would be horribly long and complex.
$$\begin{align}\overline{v_o^2}&=\overline{v_{o1}^2}+\overline{v_{o2}^2}+\overline{v_{o3}^2}+\overline{v_{o4}^2}+\overline{v_{o5}^2}\\&=|\frac{r_\pi\parallel C_\pi}{R_S+r_b+r_\pi\parallel C_\pi}g_mR_L|^2[4kTR_S+4kTr_b+2qI_B(R_S+r_b)^2]+R_L^2(2qI_C+\frac{4kT}{R_L})\end{align}$$
Now we subtitute the values of the variables into the expression. Parameters $r_\pi$ and $g_m$ are not given directly but they can be calculated using the **thermal voltage**
$$g_m=\frac{I_C}{V  _T}=\frac{100\mu A}{26mV}=3.8\times10^{-3} S$$
$$r_\pi=\frac{V_T}{I_B}=\frac{V_T\beta}{I_C}=\frac{26mV\times100}{100\mu A}=26k\Omega$$
The final result is a function of noise frequency $f$
$$\begin{align}\overline{v^2_o}&=|\frac{r_\pi\parallel C_\pi}{R_S+r_b+r_\pi\parallel C_\pi}g_mR_L|^2[4kTR_S+4kTr_b+2qI_B(R_S+r_b)^2]+R_L^2(2qI_C+\frac{4kT}{R_L})\\&=\frac{g_m^2R_L^2r^2_\pi [4kT(R_S+r_b)+2qI_B(R_S+r_b)^2]}{(R_S+r_b+r_\pi)^2+[2\pi C_\pi r_\pi  (R_S+r_b)]^2f^2}+R_L^2(2qI_C+\frac{4kT}{R_L})\\&=\frac{2.85\times 10^{-6}}{7.13\times10^{8}+1.31\times 10^{-8}f^2}+8.83\times10^{-16} \quad V^2/Hz\end{align}$$

#### 1-6  Calculate BJT Equivalent Input Noise

The model of BJT and the quivalent noise model is shown below.
![[Pasted image 20240914225454.png]]
First, we short-circuit the input port to calculate the equivalent voltage. 
$$(\frac{r_\pi//C_\pi}{r_b+r_\pi//C_\pi})^2g_m^2\overline{v^2_i}=(\frac{r_\pi//C_\pi}{r_b+r_\pi//C_\pi})^2g_m^2\overline{v^2_b}+(r_\pi//C_\pi//r_b)^2g_m^2\overline{i^2_b}+\overline{i^2_c}$$

Then, open-circuit the input port to calculate the equivalent current.
$$(r_\pi//C_\pi)^2g_m^2\overline{i^2_i}=(r_\pi//C_\pi//r_b)^2g_m^2\overline{i^2_b}+\overline{i^2_c}$$

To prevent the expression from getting too complicated, some **approximations** are applied here. Since $r_b$ is usually much smaller than $Z_\pi=r_\pi+C_\pi$, we can make the following approximation.
$$\frac{r_\pi//C_\pi}{r_b+r_\pi//C_\pi}\approx1$$
$$r_\pi//C_\pi//r_b\approx0$$

After the approximation, the expression of $\overline{v^2_i}$ and $\overline{i^2_i}$ are simplified into
$$g_m^2\overline{v^2_i}=g_m^2\overline{v^2_b}+\overline{i^2_c}$$
$$(r_\pi//C_\pi)^2g_m^2\overline{i^2_i}=\overline{i^2_c}$$
![[Pasted image 20240915104223.png]]
![[Pasted image 20240915104233.png]]
As we know, the inner noises of a BJT are given by the following equations and we usually ignore the flicker noise.
$$\overline{v_b^2}=4kTr_b$$
$$\overline{i^2_b}=2qI_B+k_1\frac{I_B^a}{f}+k_2\frac{I_B^b}{1+(f/f_c)^2}\approx2qI_B$$
$$\overline{i_c^2}=2qI_C$$
Substitute the variables of original noises in the expression of $\overline{v^2_i}$ and $\overline{i^2_i}$ and we will get
$$\overline{v^2_i}=4kTr_b+\frac{2qI_c}{g_m^2}=4kTr_b+\frac{2qI_c}{g_m}\frac{kT}{qI_c}=4kT(r_b+\frac{1}{2g_m})$$
$$(r_\pi//C_\pi)^2g_m^2\overline{i^2_i}=\overline{i^2_c}$$



#### 1-7  Calculate FET Equivalent Input Noise



#### 1-8  Calculate Equivalent Input Noise Voltage of a Op Amp Amplifier

This is a simple Op Amp based negative-feedback amplifier. Try doing noise analysis on it and find the equivalent input noise voltage source.

![[Pasted image 20240916101154.png]]

> [!FAQ] Why can we equate the noises into only one source here?
> Because we already know that the input is not open-circuited.

The noise model of the circuit is given by the graph here. The Op Amp contains three noise sources and the three external resistors contributes another three thermal noises.

$$\begin{align}\overline{e_p^2}&=4kTR_p\\\overline{e_1^2}&=4kTR_1\\\overline{e_2^2}&=4kTR_2\end{align}$$
![[Pasted image 20240916104255.png]]
Make use of the virtual-short and virtual-open principle of the Op Amp and the superposition principle, we are easily write down the total output noise.
$$\begin{align}\overline{v^2_o}&=(\frac{R_1+R_2}{R_1})^2\overline{e_p^2}+(\frac{R_2}{R_1})^2\overline{e^2_1}+\overline{e^2_2}+(\frac{R_1+R_2}{R_1})^2R_p^2\overline{i_n^2}+R_2^2\overline{i^2_n}+(\frac{R_1+R_2}{R_1})^2\overline{e_n^2}\\&=(\frac{R_1+R_2}{R_1})^2(\overline{e_p^2}+R_p^2\overline{i_n^2}+\overline{e_n^2})+(\frac{R_2}{R_1})^2\overline{e^2_1}+\overline{e^2_2}+R_2^2\overline{i^2_n}\end{align}$$The equivalent input noise voltage locates at the non-negative input.

![[Pasted image 20240916114030.png]]
$$\begin{align}(\frac{R_1+R_2}{R_1})^2\overline{e^2_{ni}}&=(\frac{R_1+R_2}{R_1})^2(\overline{e_p^2}+R_p^2\overline{i_n^2}+\overline{e_n^2})+(\frac{R_2}{R_1})^2\overline{e^2_1}+\overline{e^2_2}+R_2^2\overline{i^2_n}\\\overline{e^2_{ni}}&=(\overline{e_p^2}+R_p^2\overline{i_n^2}+\overline{e_n^2})+\frac{R_2^2\overline{e^2_1}+R_1^2\overline{e^2_2}+R_1^2R_2^2\overline{i^2_n}}{(R_1+R_2)^2}\\\end{align}$$
Now we substitute all the thermal noises with their expressions and replace all the $R_1, R_2$ variables with $R_n = R_1//R_2$ for simplicity
$$\begin{align}\overline{e^2_{ni}}&=(4kTR_p+R_p^2\overline{i_n^2}+\overline{e_n^2})+\frac{4kTR_2^2R_1+4kTR_1^2R_2+R_1^2R_2^2\overline{i^2_n}}{(R_1+R_2)^2}\\&=(4kTR_p+R_p^2\overline{i_n^2}+\overline{e_n^2})+\frac{R_1R_2}{R_1+R_2}(4kT+\frac{R_1R_2}{R_1+R_2}\overline{i_n^2})\\&=4kTR_p+R_p^2\overline{i_n^2}+\overline{e_n^2}+R_n(4kT+R_n\overline{i_n^2})\\&=\overline{e_n^2}+\overline{i_n^2}(R_p^2+R_n^2)+4kT(R_p+R_n)\end{align}$$
So we have the final result
$$\overline{e^2_{ni}}=\overline{e_n^2}+\overline{i_n^2}(R_p^2+R_n^2)+4kT(R_p+R_n)$$

---
## Noise Analysis