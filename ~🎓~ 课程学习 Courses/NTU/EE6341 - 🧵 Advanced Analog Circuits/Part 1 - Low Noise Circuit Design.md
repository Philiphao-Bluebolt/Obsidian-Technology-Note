
+ Introduction to Circuit Noise
	+ [[#Noise in the circuit]]
	+ [[#How to describe a Noise]]
	+ [[#Equivalent Noise Bandwidth]]
	+ [[#Types of Noise]]
	+ [[#Noise Source Transform]]
		+ [[#Combination (Sum of Square Rule)]]
		+ [[#Transform]]
+ Noise model of semiconductor components
	+ [[#Noise model of Diode]]

---
## Noise in the circuit

+ **Cause** - Unavoidable fluctuations of voltage and current in components
+ **Characteristics** - Random, Unpredictable, Indeterministic
+ Noise Floor - Sensitivity of a system

High Noise Floor results in inability to distinguish signal and noise

---
## How to describe a Noise

> Random process against a random signal.

+ Probability Density Function (PDF) - Time Domain Characteristics 
+ Power Spectral Density (PSD) - Frequency Domain Characteristics

In a electrical circuit, a noise emerges in the form of voltage or current, but we're more interested in the power it produces rather than its own value. The definition of power and energy of a signal in signal processing is slightly different from their counterpart in physics as **the load is ignored**.

The square of the value of a noise $x(t)$ is equal to the power in quantity.

+ Noise Power (MS Intensity) - The average **power** of a noise $x(t)$ over a long period of time
$$\overline{X^2}=\lim_{T\to\infty}\frac{1}{T} \int_0^T x^2(t)dt$$
+ RMS - The root of Noise Power, a common representation for electric signal (Unit: $V$ or $A$)
$$X_{rms}=\sqrt{\bar{X^2}}$$
+ Power Spectral Density (PSD) - A function of frequency (Unit: $V^2/Hz$ or $A^2/Hz$)
$$\overline{x^2(t)}=\frac{\overline{X^2}}{\Delta f}$$
$\Delta f$ is the equivalent noise bandwidth of the system

---
## Equivalent Noise Bandwidth

Equivalent Noise Bandwidth $\Delta f$ defines a ideal retangular window filter with a gain equal to the original system mid-frequency gain $A_0$. The total power of this ideal retangular window filter is the same as the original system
$$\begin{align}{A_0}^2\Delta f&=\int_0^\infty |A(jf)|^2df\\
\Delta f&=\frac{\int_0^\infty |A(jf)|^2df}{{A_0}^2}\end{align}$$
![[Pasted image 20240816172127.png]]

This conception is to simplify the calculation of output RMS voltage. 


---
## Types of Noise

Noises in a circuit result from different physical property.

| Noise Type                                  | Related Component                    | Cause                                | Condition of Present                  | PSD (Power Spectral Density)                  |
| ------------------------------------------- | ------------------------------------ | ------------------------------------ | ------------------------------------- | --------------------------------------------- |
| **Thermal** noise (Johnson–Nyquist noise)   | Resistor                             | Electron thermal agitation           | No (always present)                   | $$\overline{v^2}=4kTR$$                       |
| **Shot** noise                              | PN Junction (Inside Diode, BJT, MOS) | Electron crosses a potential barrier | DC biasing current exists             | $$\overline{i^2}=2qI$$                        |
| **Burst** noise (Popcorn noise)             | Dicrete Transistors                  | Heavy-metal ion<br>contamination     | DC biasing current exists             | $$\overline{i^2}=k_2\frac{I^b}{1+(f/f_c)^2}$$ |
| **Flicker** noise ($1/f$ noise)             | All devices                          | Imperfections in manufacturing       | DC biasing current exists             | $$\overline{i^2}=k_1\frac{I^a}{f}$$           |
| **Excess** Noise (One of the Flicker noise) | Resistor                             | Imperfections in manufacturing       | DC voltage across the resistor exists | $$\overline{v^2}=\frac{m^2 V^2}{f}$$          |

---
## Noise Source Transform

Similar to regular signal source, noise source can be combined together using basic principles. The direction of the noise source is not important as the noise is completely random.

### Combination (Sum of Square Rule)

Different noise sources in a circuit are uncorrelated, therefore the noise signals can be summed. The combination formula of the noise PSD:
$$\begin{align}\overline{x^2}=\overline{(x_1+x_2)^2}&=\overline{x_1^2}+\overline{x_2^2}+2\overline{x_1 x_2}\\
&=\overline{x_1^2}+\overline{x_2^2}\end{align}$$
Combination can be done between **serial voltage noise sources** and **parallel current noise sources**

![[Pasted image 20240820151158.png]]
![[Pasted image 20240820151114.png]]

### Transform

Noise generated from a resistor can be transformed between voltage form and current form using the source transform theorem.

![[Pasted image 20240820151225.png]]

---
## Noise model of Diode

The noise of a diode has two part, the thermal noise is produced by the resistance of the silicon and the other is the PN junction noise.

+ Silicon Resistance $r_s$ (equivalent to a physical resistor) - **Thermal** Noise
$$\overline{v_s^2}=4kTr_s$$
+ PN Junction - **Shot** + **Flicker** + **Burst** Noise
$$\overline{i^2}=2qI_D+k1(\frac{I_D^a}{f})+k_2\frac{I_D^b}{1+(f/f_c)^2}$$
![[Pasted image 20240820153609.png]]

---
## Noise model of BJT

The BJT noise model is based on the Hybrid Pi model

