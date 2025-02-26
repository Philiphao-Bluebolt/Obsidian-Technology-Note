+ [[#Tutorial 4 - Op Amp Noise Analysis]]
	+ [[#Queations]]
	+ [[#Solutions]]
	+ [[#4-1 Op Amp equivalent input RMS voltage and input SNR]]
	+ [[#4-2 Usage of Op Amp equivalent input noise]]

---
## Queations

![[EE4341 T4.pdf]]

---
## Solutions

![[T4 Guide(1).pdf]]


---
## 4-1  Op Amp equivalent input RMS voltage and input SNR

A signal source with $V_s = 5 mV$ will be connected to the amplifier circuit designed with Op Amp. Assume that the amplifier circuit is a ideal low pass filter for noise within $\Delta f =20 kHz$. Boltzmann’s constant $k = 1.38 \times 10^{‐23} J/K$ and $T = 300 K$ and $R_3=600\Omega$

+ (a) Obtain total equivalent RMS noise voltage at the non‐inverting input of the Op Amp
+ (b) Determine the SNR

Solve the questions for

1. Op Amp $\mu A741$ 
2. Op Amp $SE5534$
3. Non-inverting Amplifier
4. Inverting Amplifier (Gain $A=10$)


![[Pasted image 20240916155043.png]]
### (a) $\mu A741$

#### Non-inverting Amplifier

For the non-inverting amplifier, its noise model equivalent noise model is shown below

![[Pasted image 20240916162534.png]]

$$\begin{align}(\frac{R_1+R_2}{R_1})^2\overline{e^2_{ni}}&=(\frac{R_1+R_2}{R_1})^2(\overline{e_3^2}+R_3^2\overline{i_n^2}+\overline{e_n^2})+(\frac{R_2}{R_1})^2\overline{e^2_1}+\overline{e^2_2}+R_2^2\overline{i^2_n}\\\overline{e^2_{ni}}&=(\overline{e_3^2}+R_3^2\overline{i_n^2}+\overline{e_n^2})+\frac{R_2^2\overline{e^2_1}+R_1^2\overline{e^2_2}+R_1^2R_2^2\overline{i^2_n}}{(R_1+R_2)^2}\\\end{align}$$

> [!FAQ] How does cancellation of bias work?
> The bias here refers to the common mode input signal.

To cancel out the DC bias current, we make 
$$R_1 // R_2 =R_n= R_3$$
Which means
$$\begin{align}\overline{e^2_{ni}}&=\overline{e_n^2}+\overline{i_n^2}(R_3^2+R_n^2)+4kT(R_3+R_n)\\&=\overline{e_n^2}+2R_3^2\overline{i_n^2}+8R_3kT\\&=8.1\times10^{-16}\quad V^2/Hz\end{align}$$
The total RMS input noise voltage is
$$V_{rms}=\sqrt{\overline{e^2_{ni}}\Delta f}=4.0\times10^{-6}V=4 \mu V$$

The input SNR of the amplifier 
$$SNR_i(dB)=10\log\frac{V_i^2}{V_{rms}^2}=20log\frac{V_i}{V_{rms}}=1.56\times10^{22}=61.93dB$$

#### Inverting Amplifier

Since the equivalent input noise $\overline{e^2_{ni}}$ is located at the non-inverting input node, we need to equate it to the inverting input node.

![[Pasted image 20240920145201.png]]
$$\overline{e^2_{ni}}\frac{R_1+R_2}{R_1}=\overline{e^2_{nni}}\frac{R_2}{R_1}$$
$$\overline{e^2_{nni}}=\frac{R_1+R_2}{R_2}\overline{e^2_{ni}}$$
The required inverting gain is 10, so $R_2=10R_1$
$$\overline{e^2_{nni}}=1.1\overline{e^2_{ni}}=8.9\times10^{-16}\quad V^2/Hz$$
$$V_{nrms}=\sqrt{\overline{e^2_{nni}}\Delta f}=4.22\times10^{-6}=4.22 \mu V$$
The inverting input SNR of the amplifier 
$$SNR_{ni}(dB)=20log\frac{V_i}{V_{nrms}}=61.47dB$$

### (b) $SE5534$

Luckily, the replacement of Op Amp doesn't change the input signal model or noise model at all. Only the Op Amp internal noise sources $\overline{i^2_n}, \overline{v^2_n}$ are changed, affecting the PSD and RMS of equivalent input noise.

#### Non-inverting Amplifier

$$\overline{e^2_{ni}}=\overline{e_n^2}+2R_3^2\overline{i_n^2}+8R_3kT=3.59\times10^{-17}\quad V^2/Hz$$
$$SNR_i(dB)=20log\frac{V_i}{\sqrt{\overline{e^2_{ni}}\Delta f}}=75.42dB$$
#### Inverting Amplifier

$$\overline{e^2_{nni}}=1.1\overline{e^2_{ni}}=3.95\times10^{-17}\quad V^2/Hz$$
$$SNR_{ni}(dB)=20log\frac{V_i}{\sqrt{\overline{e^2_{nni}}\Delta f}}=75.00dB$$

---
## 4-2  Usage of Op Amp equivalent input noise

The circuit is designed to give an output $v_o = 2(v_1 - v_2 - v_3)$, where $v_1$, $v_2$ and $v_3$ are the input voltages.

The Op Amp has a GBW product of $10^6$ 
(Note: GBW = ‐3dB bandwidth of the amplifier multiplies mid‐band voltage gain of the amplifier). 

The equivalent input voltage and current noise spectral densities for the op amp are:
$$\overline{v^2_n}=e^2_{nw}(\frac{f_{ce}}{f}+1) \quad e_{nw}=20nV/\sqrt{Hz} \quad f_{ce}=200Hz$$
$$\overline{i^2_n}=i^2_{nw}(\frac{f_{ci}}{f}+1) \quad i_{nw}=0.5pA/\sqrt{Hz} \quad f_{ce}=2000Hz$$
(Boltzmann’s constant $k = 1.38 \times 10^{‐23} J/K$ and $T = 300 K$ and $R_1 = R_3 = 10 k\Omega$)

+ (a) Determine the values of resistors $R_2$, $R_4$ and $R_F$
+ (b) Obtain the RMS and peak‐to‐peak output noise voltage above $1Hz$

![[Pasted image 20240917012223.png]]
#### (a)

Assume that the Op Amp input voltage is $v_i$ , the following equations describes the voltages relationship.
$$v_i=\frac{R_3}{R_3+R_4}v_1$$
$$\frac{v_3-v_i}{R_1}+\frac{v_2-v_i}{R_2}=\frac{v_i-v_o}{R_F}$$
So we have 
$$\begin{align}v_o&=(1+\frac{R_F}{R_1}+\frac{R_F}{R_2})\frac{R_3}{R_3+R_4}v_1-\frac{R_F}{R_2}v_2-\frac{R_F}{R_1}v_3\\&=2v_1-2v_2-2v_3\end{align}$$
Then
$$\begin{cases}R_F=20k\Omega\\R_2=10k\Omega\\R_4=15k\Omega\end{cases}$$

#### (b)

Previously, we already derived the equation of equivalent input noise voltage for a typical Op Amp negative feedback circuit. 
$$\overline{e^2_{ni}}=\overline{e_n^2}+\overline{i_n^2}(R_p^2+R_n^2)+4kT(R_p+R_n)$$
In the circuit here, we have
$$R_p=R_3//R_4=6k\Omega$$
$$R_n=R_1//R_2//R_F=4k\Omega$$
