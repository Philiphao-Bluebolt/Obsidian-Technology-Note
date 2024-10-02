+ **What is it?** - a modern approach for analysis and design of control systems. 
+ **Advantages**
	+ **Programming Friendly** - Easy inplementation on computer
	+ **Wider Application** - applicable to non-linear and time-varying systems 

+ Continuous System
	[[#State Space Equation]]
	[[#Convert to Transform Function]]
	[[#Time Domain Solution]]
+ Discrete System

---
## State Space Equation

Unlike transfer function, which only focuses on the input-output relationship, describing a black box model, state space analysis focuses on a series of internal state variables $x_1, x_2, ...$ and describes their changes using the state space equation.
![[Pasted image 20240923145432.png]]
+ Definition
$$\begin{cases}\dot{x}(t)=Ax(t)+Bu(t)\\ \\y(t)=Cx(t)+Du(t)\end{cases}$$
+ $A$ - transfer matrix
+ B - input matrix
+ C - output matrix
+ D - inout matrix

---
## Convert to Transform Function

Apply laplace transform on both the state transfer equation and the output equation and eliminate the state vectors $x(t)$.
$$\begin{cases}sX(s)=AX(s)+BU(s)\\ \\Y(s)=CX(s)+DU(s)\end{cases}$$
$$\frac{Y(s)}{U(s)}=C(sI-A)^{-1}B+D$$
---
## Time Domain Solution


$$x(t)=e^{A(t-t_0)}x(t_0)+\int_{t_0}^te^{A(t-\tau)Bu(\tau)d\tau} \quad (t\geq t_0)$$





---
## Similarity Transformation