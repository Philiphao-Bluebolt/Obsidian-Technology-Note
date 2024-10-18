+ **What is it?** - a modern approach for analysis and design of control systems. 
+ **Advantages**
	+ **Programming Friendly** - Easy inplementation on computer
	+ **Wider Application** - applicable to non-linear and time-varying systems 

+ Continuous System Basis
	+ [[#State Space Equation]]
	+ [[#Convert to Transform Function]]
	+ [[#State Transition Equation]]
	+ [[#Similarity Transformation]]
+ Discrete System Basis
	+ [[#Discrete State Space Model]]
	+ [[#Convert to Discrete Pulse Transfer Function]]
	+ [[#Discrete Poles and Zeros]]
	+ [[#Discrete State Transition Equation]]
+ Controller and Observer
	+ [[#Similar State Spaces]]
	+ [[#Controllability and Observability]]
	+ [[#Canonical Form]]
		+ [[#From the Transform Function]]
	+ [[#Loss of Controllability or Observability by sampling]]
	+ [[#State Feedback Controller Design]]
		+ [[#Ackmann's Formula]]
	+ [[#Dead-beat Control]]

---
## State Space Equation

Unlike transfer function, which only focuses on the input-output relationship, describing a black box model, state space analysis focuses on a series of internal state variables $x_1, x_2, ...$ and describes their changes using the state space equation.
![[Pasted image 20240923145432.png]]
+ Definition
$$\begin{cases}\dot{x}(t)=Ax(t)+Bu(t)\\ \\y(t)=Cx(t)+Du(t)\end{cases}$$
+ $A$ - transfer matrix
+ B - input matrix
+ C - output matrix
+ D - feed-forward matrix

---
## Convert to Transform Function

+ **Goal** - State Space Model --> Transform Function
+ **Method** - Laplace Transform then eliminate state variables.

State Space Model of a system can be converted into a transform function through Laplace transform.

Apply Laplace transform on both the state transfer equation and the output equation.

$$\begin{cases}\dot{x}(t)=Ax(t)+Bu(t)\\ \\y(t)=Cx(t)+Du(t)\end{cases}\quad\to\quad\begin{cases}sX(s)=AX(s)+BU(s)\\ \\Y(s)=CX(s)+DU(s)\end{cases}$$

Eliminate the state vectors $x(t)$ and we get the expression
$$\frac{Y(s)}{U(s)}=C(sI-A)^{-1}B+D$$
---
## State Transition Equation

+ **Goal** - Time --> State
+ **Method** - Laplace Transform then Inverse Laplace

Since the state space equation doesn't explicitly describe every state of the system, we need to find an approach to derive the state $x(t)$ directly from time $t$

First we apply Laplace Transform to the state equation.

$$\begin{align}\mathcal{L}\{\dot{x}(t)\}&=\mathcal{L}\{Ax(t)+Bu(t)\}\\sX(s)-x(0)&=AX(s)+BU(s)\\X(s)&=(sI-A)^{-1}BU(s)+(sI-A)^{-1}x(0)\end{align}$$

Apply inverse Laplace transform to the expression
$$x(t)=\Phi(t) x(0)+\int_0^t \Phi(t-\tau)Bu(\tau)d\tau$$
The state transition matrix $\Phi(t)$ is defined as
$$\Phi(t)=\mathcal{L}^{-1}\{(sI-A)^{-1}\}=e^{At}$$
 It's not necessary to derive $x(t)$ based on $x(0)$, any state value $x(t_0)$ before $t$ is usable. This is what we call state transition equation.
$$x(t)=\Phi(t) x(t_0)+\int_{t_0}^t \Phi(t-\tau)Bu(\tau)d\tau \quad t>t_0$$

---
## Discrete State Space Model

+ **Goal** - Derive the discrete equation of a state space from its continuous equation

In a digital control system, the controlled object or the plant is usually continuous and receives the control signal from the DAC. A discrete version of the controlled object's state space model can be built in such condition.

$$\begin{cases}\dot{x}(t)=Ax(t)+Bu(t)\\ \\y(t)=Cx(t)+Du(t)\end{cases} \quad \to \quad \begin{cases}x(k+1)=A'x(k)+B'u(k)\\ \\y(k)=C'x(k)+D'u(k)\end{cases}$$

The discrete version of a continuous time state space is given by the following equations

$$\begin{cases}\dot{x}(t)=Ax(t)+Bu(t)\\ \\y(t)=Cx(t)+Du(t)\end{cases} \quad \to \quad \begin{cases}x(k+1)=\Phi(T)x(k)+(\int_0^T\Phi(\tau)d\tau B) u(k)\\ \\y(k)=Cx(k)+Du(k)\end{cases}$$

+ Sampling Time Period $T$
+ State Transition Matrix $\Phi(t)=\mathcal{L}^{-1}\{(sI-A)^{-1}\}$

---
## Convert to Discrete Pulse Transfer Function

+ **Goal** - Get the discrete time transfer function from a discrete state space
+ **Method** - Z Transform then eliminate state variables.

The calculation of discrete time transfer function is similar to its continuous counterpart. Just replace Laplace transform with Z transform.

$$\begin{cases}x(k+1)=Ax(k)+Bu(k)\\ \\y(k)=Cx(k)+Du(k)\end{cases}\quad\to\quad\begin{cases}zX(z)=AX(z)+BU(z)\\ \\Y(z)=CX(z)+DU(z)\end{cases}$$

Eliminate the state vectors $x(k)$ and we get the expression
$$\frac{Y(z)}{U(z)}=C(zI-A)^{-1}B+D$$

---
## Discrete Poles and Zeros

The poles of a discrete state space system are identical to the eigenvalues of discrete transfer matrix $A$ and can be obtained by solving the following equation
$$det(z_pI-A)=0$$
The zeros of a discrete state space system
$$det\begin{bmatrix}z_0I-A &-B\\C&D\end{bmatrix}=0$$


---
## Discrete State Transition Equation

Unlike its continuous counterpart, discrete state transition equation can be derived directly by recursion, thus simpler 
$$\begin{align}x(1)&=Ax(0)+Bu(0)\\x(2)&=Ax(1)+Bu(1)\\x(3)&=Ax(2)+Bu(2)\\&...\end{align}$$
Each state value can be recursively represented by the initial state and the previous inputs
$$\begin{align}x(1)&=Ax(0)+Bu(0)\\x(2)&=A^2x(0)+ABu(0)+Bu(1)\\x(3)&=A^3x(0)+A^2Bu(0)+ABu(1)+Bu(2)\\&...\\x(k)&=A^kx(0)+\sum_{i=0}^{k-1}A^{k-1-i}Bu(i)\end{align}$$

---
## Similar State Spaces

+ **Representation** - State Spaces of the same system
+ **Related Concept** - Similar Matrix 

Similar State Spaces describe the same system with different state variables, they share the **same** transfer function and characteristic polynomial. Their difference is due to different choices of internal state variables.
 
Similarity Transformation converts a state space into one of its similar space.

$$\begin{cases}x(k+1)=Ax(k)+Bu(k)\\ \\y(k)=Cx(k)+Du(k)\end{cases} \quad\to\quad \begin{cases}w(k+1)=A_ww(k)+B_wu(k)\\ \\y(k)=C_ww(k)+D_wu(k)\end{cases}$$
$$\begin{cases}w(k)=P^{-1}x(k)\\A_w =P^{-1}AP\\B_w=P^{-1}B\\C_w=CP\\D_w=D\end{cases}$$
A non-singular matrix $P$ is used in the transform. Actually, the term "similar" is a concept borrowed from linear algebra, the state transfer matrix $A$ of similar state spaces are similar matrices


---
## Controllability and Observability

If the following controllability matrix has rank $n$ (full rank), then the system whose state transfer function is described by $A,B$ is controllable.
$$W_C=\begin{bmatrix}B&AB&A^2B&\dots&A^{n-1}B\end{bmatrix}$$
If the following observability matrix has rank $n$ (full rank), then the system whose has transfer matrix $A$ and output matrix $C$ is observable.
$$W_O=\begin{bmatrix}C\\CA^2\\\vdots\\CA^{n-1}\end{bmatrix}$$

---
## Canonical Form

There exists two canonical form that any system can transformed into: The **Controllable Canonical Form** and the **Observable Canonical Form**. The state transfer matrix of the two forms is related by transpose

Assume that the characteristic polynomial of the discrete system $(A,B,C,D)$ is given by
$$|\lambda I-A|=\lambda^n+a_{n-1}\lambda^{n-1}+...+a_2\lambda^2+a_1\lambda+a_0$$
+ Controllable Canonical Form (CCF)
$$A_C=\begin{bmatrix}0&1&0&0&...&0\\0&0&1&0&...&0\\0&0&0&1&...&0\\\vdots&\vdots&\vdots&\vdots&\ddots&\vdots\\0&0&0&0&...&1\\-a_0&-a_1&-a_2&-a_3&\dots&-a_{n-1}\end{bmatrix}\quad\quad B_C=\begin{bmatrix}0\\0\\0\\\vdots\\0\\1\end{bmatrix}$$
+ Observable Canonical Form (OCF)
$$A_O=\begin{bmatrix}0&0&\dots&0&-a_0\\1&0&\dots&0&-a_1\\0&1&\dots&0&-a_2\\\vdots&\vdots&\ddots&\vdots&\vdots\\0&0&\dots&1&-a_{n-1}\end{bmatrix}\quad\quad C_O=\begin{bmatrix}0&0&0&\dots&0&1\end{bmatrix}$$

The transform matrix $P$ mapping the system into its CCF is defined in following equation in which $W_C$ is the original controllability matrix and $\tilde{W}_C$ is the CCF controllability matrix
$$P=W_C\tilde{W}_C^{-1}$$

The transform matrix for OCF is similar.
$$P=W_O^{-1}\tilde{W}_O$$

### From the Transform Function




---
## Loss of Controllability or Observability by sampling


---
## State Feedback Controller Design


### Ackermann's Formula

Ackermann's Formula provides a simple expression for the state feedback controller
$$K=\begin{bmatrix}0&\dots&0&1\end{bmatrix}W_C^{-1}\alpha_C(A)$$
+ $\begin{bmatrix}0&\dots&0&1\end{bmatrix}$ is a $1\times n$ matrix 
+ $W_C$ is the controllability matrix
+ $\alpha_C(A)$ is the desired characteristic polynomial whose eigenvalue variables are replaced by state transfer matrix $A$
$$\alpha_C(A)=A^n+\beta_{1} A^{n-1}+...++\beta_{n}I$$
---
## Dead-beat Control

