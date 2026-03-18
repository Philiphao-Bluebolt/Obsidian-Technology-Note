+ [[#Tutorial 2 - Diode and BJT noise model]]
	+ [[#Queations]]
	+ [[#Solutions]]
	+ [[#2-1 Diode circuit noise analysis]]
	+ [[#2-2 BJT circuit noise analysis]]

---
## Queations

![[EE4341 T2 1.pdf]]

---
## Solutions

![[T2 Guide(1).pdf]]

---
## 2-1  Diode circuit noise analysis

Assume that $V_D = 0.60V$. Boltzmann's constant $k = 1.38 \times 10^{-23}J/K$, $q = 1.6\times10^{-19} C$ and $T = 300K$.

+ (a) Calculate the mean-squared noise-voltage spectral density in $V^2/Hz$ at $v_o$ for the circuit and then calculate the RMS noise voltage in a $100 kHz$ equivalent noise bandwidth. Neglect capacitive effects, flicker noise and series resistance in the diode.

+ (b) If a $1000 pF$ capacitor is now connected across the diode, including flicker noise, calculate and plot the output mean-­squared noise voltage spectral density at $v_o$ in $V^2/Hz$ on log scales from $f = 1Hz$ to $f =10 MHz$. Flicker noise spectral density $= 3 \times 10^{-16}(I_D/f) A^2/Hz$.

![[Pasted image 20240908102455.png]]

First, we draw the equivalent noise circuit without the diode serial resistance and its noise.

![[Pasted image 20240908112330.png]]

The total noise PSD can be computed by the following equation, however we don't know the equivalent resistance $r_d$ and DC current $I_D$ of the diode.
$$\begin{align}\overline{v^2_o}&=(r_d\parallel R)^2(\overline{i^2_R}+\overline{i^2})\\&=(\frac{r_d R}{r_d + R})^2(\frac{4kT}{R}+2qI_D)\end{align}$$
Now calculate $I_D$ and $r_d$. As we know that the voltage drop of silicon diode $V_D=0.6V$, the DC current flowing through the circuit is
$$I_D=\frac{10V-0.6V}{20k\Omega}=0.47mA$$
The equivalent resistance $r_d$ is not fixed but is stable when the DC current is fixed
$$r_d=\frac{kT}{qI_D}=55.05\Omega$$
Now we can calculate $\overline{v^2_o}$
$$\overline{v^2_o}=4.558\times10^{-19}\quad V^2/Hz$$
The RMS noise voltage is
$$V_{rms}=\sqrt{\overline{v^2_o}\Delta f}=0.21\mu V$$

Now we consider the effect of the flicker noise and the extra capacitor.

![[Pasted image 20240908120432.png]]
The new capacitor doesn't affect the DC current of the circuit, but it change the equation of the output noise PSD
$$\begin{align}\overline{v^2_o}&=(r_d\parallel R\parallel C)^2(\overline{i^2_R}+\overline{i^2})\\&=|\frac{1}{\frac{1}{R}+\frac{1}{r_d}+j2\pi fC}|^2(\frac{4kT}{R}+2qI_D+k_1\frac{I_D^a}{f})\\&=\frac{R^2r_d^2}{r_d^2+2r_dR+R^2+4\pi ^2C^2R^2 r_d^2f^2} (1.51\times10^{-22}+\frac{1.41\times10^{-19}}{f})\\&=\frac{1.21\times10^{12}}{4.02\times10^8+4.79\times10^{-5}f^2}(1.51\times10^{-22}+\frac{1.41\times10^{-19}}{f})\end{align}$$

The frequency response of $\overline{v_o^2}$ has two cutoff frequency $f_1, f_2$, the following equations show how they're calculated.
$$\begin{align}1.51\times10^{-22}&=\frac{1.41\times10^{-19}}{f_2}\\f_1&=933.77Hz\end{align}$$
$$\begin{align}4.79\times10^{-5}f_1^2&=4.02\times10^8\\f_2&=2.897MHz\end{align}$$

Now draw the approximate bode plot, the lowest frequency in the graph could be $1Hz$
$$\overline{v^2_o}|_{f=1Hz}=4.2\times10^{-16} V^2/Hz$$
![[Pasted image 20240916145120.png]]

---
## 2-2  BJT circuit noise analysis

The amplifier circuit has a $-3dB$ bandwidth of $10 kHz$ (single-pole response).
Boltzmann's constant $k = 1.38 \times 10^{-2}J/K$, $q = 1.6\times10^{-19} C$ and $T = 300K$. 
BJT parameters $\beta=150$, $r_{bb'}=60\Omega$.
Ignore flicker noise and the thermal noise of the load resistance.

+ (a) Determine the value of $V_S$ so that $SNR = 0 dB$.
+ (b) Show that if a BJT is driven from a signal source with a source resistance Rs, the value of biasing collector current for maximum sensitivity is given by the following expression.
+ (c) Determine the value of biasing $I_c$ for max $SNR$ and obtain $V_S$ for $SNR = 0 dB$ under the new biasing condition.
![[Pasted image 20240921152749.png]]

### (a) 


