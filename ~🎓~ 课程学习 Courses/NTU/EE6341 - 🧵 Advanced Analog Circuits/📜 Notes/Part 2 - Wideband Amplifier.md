+ **Goal** - Extent the bandwidth of an BJT amplifier circuit

The frequency characteristics of BJT amplifier circuits are unable to neglect when the input signal frequency becomes high. The PN junction capacitance inside the BJT would cause a gain decay in high frequency.

+ [[#Miller Effect]]
+ [[#BJT High Frequency Model]]
	+ [[#Hybrid-pi Model]]
	+ [[#T Model]]
+ [[#BJT Amplifier Frequency Response]]
	+ [[#Common-emitter]]
	+ [[#Cascode of Common-emitter and Common-base]]
+ [[#Feedback for Wideband]]

---
## Miller Effect

+ **Function** - Break the input-output bridge capacitance into the input part and output part, greatly simplify the frequency analysis of amplifiers.

Miller Effect is a useful phemonemon regarding bridge capacitance of an amplifier. It describes the equipvalent of the bridge capacitance from the input and output aspect respectively.

Assume there's an amplifier circuit with voltage gain $A$, the capacitance $C$ bridging over the input and output nodes can be seperated into two parts. ($A$ can be negative for inverting amplifier)

+ Input equivalent is amplified to $C(1-A)$
+ Output equivalent is reduced to $C(1-\frac{1}{A})$

![[Pasted image 20241129152743.png]]

Miller Effect greatly simplies the calculation of frequency response at the cost of some mild approximation. 

---
## BJT High Frequency Model

The classical models now include two capacitors representing the base-emitter and base-collector PN junction capacitance respectively. 

### Hybrid-pi Model



![[Pasted image 20241129175807.png]]

### T Model

![[Pasted image 20241129175855.png]]




---
## BJT Amplifier Frequency Response

Here we use Miller Effect to simply the analysis of universal frequency response. Without Miller Effect, it would be painful to factorize the impedance polynomial into frequency factors.

### Common-emitter




### Cascode of Common-emitter and Common-base 

---
## Feedback for Wideband

The introduction of feedback circuits can broaden the bandwidth of an amplifier at the cost of lower gain. 

Consider the following closed-loop system in which $G(j\omega)$ and $H(j\omega)$ are the transfer functions of the main amplifier and the feedback circuit respectively. The main amplifier is first-ordered with gain $A_o$ and cut-off frequency $\omega_o$
$$G(j\omega)=\frac{A_o}{1+j\frac{\omega}{\omega_o}}$$
![[Pasted image 20241130144950.png]]
The closed-loop system can be written as
$$G_{cl}(j\omega)=\frac{G(j\omega)}{1+HG(j\omega)}=\frac{\frac{A_o}{1+j\frac{\omega}{\omega_o}}}{1+\frac{A_o H}{1+j\frac{\omega}{\omega_o}}}=\frac{A_o}{1+j\frac{\omega}{\omega_o}+A_oH}=\frac{\frac{A_o}{1+A_oH}}{1+j\frac{\omega}{\omega_o(1+A_oH)}}$$
While the GBP stay unchanged:

+ The gain is reduced by the factor of ($1+A_oH$) , usually approximated as $\frac{1}{H}$
$$A_{ocl}=\frac{A_o}{1+A_oH}\approx\frac{1}{H}$$
+ The cut-off frequency is enlarged by the factor of ($1+A_oH$)  
$$\omega_{ocl}=\omega_o(1+A_oH)$$

The feedback configurations are catagorized into four types based on their output measurement and what input they are affecting. Remember, you don't want the feedback circuits to change the output value. Instead, they must affect the input value.

+ **Shunt** means connecting in parallel, dividing the currents but sharing the same voltage
	+ **Measuring Voltage**
	+ **Changing Current**
+ **Series** means connecting in serial, dividing the voltage but sharing the same current
	+ **Measuring Current**
	+ **Changing Voltage**

The first word implys the feedbacking configuration at the input and the second word implys the 
measuring configuration at the output

| Amplifier Input | Amplifier Output | Amplifier Transfer Function | Feedback Configuration |
| :-------------: | :--------------: | :-------------------------: | :--------------------: |
|     Voltage     |     Voltage      |      Transfer Voltage       |      Series-Shunt      |
|     Current     |     Voltage      |       Transresistance       |      Shunt-Shunt       |
|     Voltage     |     Current      |      Transconductance       |     Series-Series      |
|     Current     |     Current      |      Transfer Current       |      Shunt-Series      |
