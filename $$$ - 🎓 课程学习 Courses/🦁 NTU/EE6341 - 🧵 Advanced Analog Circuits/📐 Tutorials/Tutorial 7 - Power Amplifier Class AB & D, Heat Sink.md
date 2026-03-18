+ [[#Tutorial 7 - Power Amplifier Class AB, D and Heat Sink]]
	+ [[#Questions]]
	+ [[#Solutions]]
	+ [[#7-1 Instantaneous value calculation of Class AB]]
	+ [[#7-2 Class D]]
	+ [[#7-3 Heat sink]]

---
## Questions

![[EE4341-EE6341 Tutorial 7.pdf]]

---
## Solutions

![[63739592.pdf]]

---
## 7-1  Instantaneous value calculation of Class AB

### (a)

Okay, we must admit this is funny and not funny at the same time. It's completely maths and not much physics. We just simple use the transistor equations and KCL and KVL to get a bunch of equations and then try to solve it.

Each transistor fulfills three equations: KCL, Shockley Equation and the $\beta$ relationship. It means that there is only one unknown value for every pair of $I_C,I_B,I_E,V_{BE}$
$$\begin{cases}I_E=I_C+I_B\\V_{BE}=V_T\ln\frac{I_C}{I_S}\\I_C=\beta I_B\end{cases}$$
Each diodes fulfills the Shockley Equation. It means that ther is only one unknown value for a diode.
$$V_D=V_T\ln\frac{I_D}{I_S}$$
![[Pasted image 20241110222135.png]]
Firstly, we use KVL on $Q_1,Q_3$ and two diodes
$$V_{BB}=V_{BE1}+V_{BE3}$$
+ $V_{BB}$ can be related to $I_{E1}$ through:
$$\begin{cases}V_{BB}=2V_T\ln\frac{I_D}{I_S}\\I_{B1}=I_{bias}-I_D\\I_{E1}=(1+\beta)I_{B1}\end{cases}$$
+ $V_{BE1}$ can be related to $I_{E1}$ through:
$$\begin{cases}I_{E1}=\frac{\beta+1}{\beta}I_{C1}\\I_{C1}=I_Se^\frac{V_{BE1}}{V_T}\end{cases}$$
+ $V_{BE3}$ can be related to $I_{E1}$ through:
$$\begin{cases}I_{C3}=I_Se^\frac{V_{BE3}}{V_T}\\I_{E3}+I_{C2}=I_{E1}+I_{L}\\I_{E3}=\frac{\beta+1}{\beta}I_{C3}\\I_{C2}=\beta I_{B2}\\I_{B2}=I_{C3}\end{cases}$$
### (b)

The equation doesn't change, just let $I_L=\frac{v_o}{R_L}$

### (c)



---
## 7-2  Class D



---
## 7-3  Heat sink



