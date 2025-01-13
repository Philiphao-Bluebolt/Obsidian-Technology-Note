+ **Goal** - Inplement the digital control system using programming

Digital control systems are usually implemented by computers, thus programming is the intuitive tool for creating a real digital controller.

Another implementation is by building digital circuit

+ [[#General Form of Transfer Function]]
+ [[#Controller Coefficients Quantization Error]]
+ [[#Programming Method]]
	+ [[#Direct Programming]]
	+ [[#Standard Programming]]
	+ [[#Serial Programming]]
	+ [[#Parallel Programming]]

---
## General Form of Transfer Function

After the design is completed, all the digital controller can be written in the form of polynomial of unit delay $z^{-1}$
$$G(z)=\frac{Y(z)}{X(z)}=\frac{b_0+b_1z^{-1}+b_2z^{-2}+\dots+b_mz^{-m}}{1+a_1z^{-1}+a_2z^{-2}+\dots+a_nz^{-n}}$$
+ For causality, ensure $n\geq m$ 
+ Coefficient $a$ and $b$ are constants

---
## Controller Coefficients Quantization Error

While implementing, the word length limit of the microprocessor forces quantization of the coefficients, making the zeros and poles change and creating quantization errors

By breaking the high-order general transfer function of the controller intos low-order subsystems, the effect of quantization errors would be mitigated. Two of the programming methods are serial and parallel programming

---
## Programming Method

While programming the controller, total delay and quantization error should be minimized.

### Direct Programming

+ Total Delay - $m+n$

Direct programming obtains the output by adding up $m$ input feed-forward values and $n$ output feedback feedback values. This method is intuitive but seldom used because of the high total delay and quantization.

+ Equation
$$\begin{align}Y(z)&=(b_0+b_1z^{-1}+\dots+b_mz^{-m})X(z)-(a_1z^{-1}+\dots+a_nz^{-n})Y(z)\\&=[b_0X(z)+b_1z^{-1}X(z)+\dots+b_mz^{-m}X(z)]-[a_1z^{-1}Y(z)+\dots+a_nz^{-n}Y(z)]\end{align}$$
+ Graph
![[Pasted image 20241121122911.png]]
### Standard Programming

+ Total Delay - $n$

Standard Programming used feedback to change intermediate value $H(z)$ and only use feed-forward to output. It combines the unit delays in the denominator and the numerator, thus reduces the number of delay to $n$

+ Equation ($H(z)$ is a intermediate function)
$$\begin{align}Y(z)&=(b_0+b_1z^{-1}+\dots+b_mz^{-m})H(z)\\&=b_0H(z)+b_1z^{-1}H(z)+\dots+b_mz^{-m}H(z)\end{align}$$
$$\begin{align}H(z)&=\frac{X(z)}{1+a_1z^{-1}+a_2z^{-2}+\dots+a_nz^{-n}}\\&=X(z)-a_1z^{-1}H(z)-a_2z^{-2}H(z)-\dots-a_n z^{-n} H(z)\end{align}$$
+ Graph
![[Pasted image 20241121124004.png]]
### Serial Programming

+ Total Delay - $n$

Series Programming breaks the controller into several first-order and second-order blocks, it's one of the programming methods that reduce coefficient quantization error.
$$G(z)=\prod_{i=0}^j\frac{1+b_iz^{-1}}{1+a_iz^{-1}}\times\prod_{i=j+1}^{p}\frac{1+e_iz^{-1}+f_iz^{-2}}{1+c_iz^{-1}+d_iz^{-2}}$$
The pairing of poles and zeros avoid noncausal sections of zero factors. ($b_i,e_i,f_i$ can be 0 if there's no zero)

+ The first order fractions are pairs of pole and zero
+ The second order fractions are pairs of conjugated poles and zeros.

Each blocks can be realized using standard programming

### Parallel Programming

+ Total Delay - $2$

Parallel Programming breaks the controller into parallel sums


