![[EE4341-EE6341 Home Assignment 2024 - Prof See.pdf]]

---
## Solution

### The Class AB Power Amplifier

![[Pasted image 20241021130330.png]]

### Graph of $i_{C1}$ and $i_{C2}$

![[Pasted image 20241021194530.png]]

### Graph of $v_{BB}$

![[Pasted image 20241021194707.png]]

### Graph of $i_{D}$

![[Pasted image 20241021194800.png]]

### (a) $v_i = +12\mathrm{V}$

+ Peak Value
	+ $i_{C1}=84.0113\mathrm{mA}$
	+ $i_{C2}=-452.5959\mathrm{\mu A}$
	+ $i_{D}=14.4660\mathrm{mA}$
	+ $v_{BB}=1.4751\mathrm{V}$

### (b) $v_i = 0\mathrm{V}$

+ Peak Value
	+ $i_{C1}=13.0521\mathrm{mA}$
	+ $i_{C2}=-8.3538\mathrm{mA}$
	+ $i_{D}=14.9400\mathrm{mA}$
	+ $v_{BB}=1.4304\mathrm{V}$

### (c) $v_i = -12\mathrm{V}$

+ Peak Value
	+ $i_{C1}=799.3672\mathrm{\mu A}$
	+ $i_{C2}=-75.0220\mathrm{mA}$
	+ $i_{D}=14.9968\mathrm{mA}$
	+ $v_{BB}=1.4426\mathrm{V}$

### (d)

The given Class AB amplifier is a improved version of Class B, which eliminates crossover distortion by installing two diodes between the bases of two transistors. The diodes rise up the quinscent base voltage $V_{BN}$ of $Q_N$ by two threshold turn-on voltage $V_{BE}$ of the BJTs, ensuring that both transistors are active even the transient input signal value is small.

Thoroughly, The critical input voltage of the circuit is approximately $-7.15\mathrm{V}$ at which the two transistors would switch their active state. $Q_n$ become active when the input rises above $-7.15\mathrm{V}$ and $Q_p$ become active when it drops below $-7.15\mathrm{V}$. When $v_i=-7.15\mathrm{V}$, the two diodes provide a voltage drop of $14.3\mathrm{V}$, rising the base voltage of $Q_n$ to $7.15\mathrm{V}$, thus are able to keep $Q_n$ active along with $Q_p$.

When $Q_n$ is active, the upper half of the input wave is processed. When $Q_p$ is active, the lower half is processed by $Q_p$. The two transistor output currents $I_{C1}$ and $I_{C2}$ would combine and form the load current $I_L$ at the end. Since there is no crossover distortion, the linearity of output signal is good.