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
	+ [[#Zero-pole Cancellation Effect]]
	+ [[#Loss of Controllability or Observability by sampling]]
	+ [[#State Feedback Controller Design]]
		+ [[#Pole Placement Method]]
		+ [[#Ackermann's Formula]]
		+ [[#Dead-beat Control]]
+ Observer Design
	+ [[#State Observer Introduction]]
	+ [[#Open-loop Prediction Observer]]
	+ [[#Closed-loop Prediction Observer]]
		+ [[#Pole Placement Method]]
		+ [[#Ackermann’s Formula]]
	+ [[#Reduced-order Observer]]
	+ [[#Current Observer]]
		+ [[#Ackermann’s Formula]]
	+ [[#State Observer Implementation]]
+ Optimal Control
	+ 


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

The discrete version of a continuous time state space is given by the following equations assuming the sampling is done by a **ZOH**

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
A non-singular matrix $P$ is used in the transform. Actually, the term "similar" is borrowed from linear algebra, the state transfer matrix $A$ of similar state spaces are similar matrices


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
Since the characteristic polynomial can be derived from the transfer function directly (actually it's the denominator), it's possible to obtain the canonical form from the transfer function


---
## Zero-pole Cancellation Effect

If a system's transfer function has zero-pole cancellation, the state space of the system would be either uncontrollable or unobservable. Intuitively, this is because zero-pole cancellation hides some of the internal states.

In contrast, if the system has no zero-pole cancellation, its state space is always controllable and observable.

---
## Loss of Controllability or Observability by sampling

When sampled from a continuous system, the controllability and observability could be lost for **some sampling period**.

If the continuous system is uncontrollable, then the sampled discrete system is uncontrollable. This applies to observability as well.

---
## State Feedback Controller Design

+ **Goal** - Obtain desired closed-loop poles 

State feedback is an important modern control method. It creates a path from the internal state $x(k)$ to the input $u(k)$, which will result to a change of the system's closed-loop poles. 

![[Pasted image 20241117153925.png]]
The closed-loop system state space
$$\begin{cases}x(k+1)=(A-BK)x(k)+Br(k)\\y(k)=Cx(k)+Du(k)\end{cases}$$
To obtain desired poles, the feedback gain $K$ is to be calculated.
$$K=\begin{bmatrix}k_1 & k_2 & k_3 &\dots&k_n\end{bmatrix}^T$$

### Pole Placement Method

Let the characteristic polynomial of the state feedback system equal to the desired characteristic polynomial and solve for $K$
$$\det(zI-(A-BK))=\alpha_C(z)$$
### Ackermann's Formula

Ackermann's Formula provides a simple expression for the state feedback controller, it's the matrix form of pole placement method
$$K=\begin{bmatrix}0&\dots&0&1\end{bmatrix}W_C^{-1}\alpha_C(A)$$
+ $\begin{bmatrix}0&\dots&0&1\end{bmatrix}$ is a $1\times n$ matrix 
+ $W_C$ is the controllability matrix
+ $\alpha_C(A)$ is the desired characteristic polynomial whose eigenvalue variables are replaced by state transfer matrix $A$
$$\alpha_C(A)=A^n+\beta_{1} A^{n-1}+...++\beta_{n}I$$
### Dead-beat Control

Dead-beat control is a phenomenon of discrete system. For a system with order $n$, a dead-beat controller ensures that the system will be in steady state after $n$ steps at most.

To achieve dead-beat control using state feedback, all the poles of the closed-loop system must be at the origin of the z-plane. 
$$\alpha_C(A)=A^n$$
---
## State Observer Introduction

+ **Goal** - Estimate the unmeasurable states of a system

State observer is a system intended to estimate the states of another system whose states can not be directly measured. They only work on **observable** and **stable** systems.

+ Prediction Observer predicts the next states $\overline{x}(k)$ based on $y(k-1)$
+ [[#Current Observer]] estimates the current states $\overline{x}(k)$ based on $y(k)$

---
## Open-loop Prediction Observer

The open-loop observer is a system with matrix $A,B,C$ identical to the original system but doesn't interact with it.

The state transfer equation is identical
$$\begin{cases}{x}(k+1)=Ax(k)+Bu(k)\\\bar{x}(k+1)=A\bar{x}(k)+Bu(k)\end{cases}$$
The estimation error would become 0 if the transfer matrix $A$ is stable
$$x_e(k+1)=x(k+1)-\bar{x}(k+1)=[Ax(k)+Bu(k)]-[A\bar{x}(k)+Bu(k)]=Ax_e(k)$$
$$\lim_{k\to\infty}x_e(k)=0$$


![[Pasted image 20241122100906.png]]

---
## Closed-loop Prediction Observer

The closed-loop adds a output differential feedback to the state observer
$$\begin{align}\bar{x}(k+1)&=A\bar{x}(k)+Bu(k)+L_o(y(k)-\bar{y}(k))\\&=(A-L_OC)\bar{x}(k)+Bu(k)+L_O Cx(k)\end{align}$$
The feedback gain vector $L_O$ is to be determined by desired observer poles
$$L_O=\begin{bmatrix}l_1 & l_2 & l_3 &\dots&l_n\end{bmatrix}^T$$
Since the closed-loop prediction observer is symmetric to the state feedback controller, similar approach can be used for design.


![[Pasted image 20241122111219.png]]
### Pole Placement Method

Similar to the feedback controller design, just equate the observer characteristic polynomial to the desired pole characteristic polynomial
$$\det(zI-(A-L_OC))=\alpha_O(z)$$
### Ackermann’s Formula

The Ackermann’s Formula for closed-loop prediction observer is obtained from the original one by duality of controllability and observability.
$$L_O=\alpha_O(A)W_O^{-1} \begin{bmatrix}0\\\vdots\\0\\1\end{bmatrix}$$

+ $\alpha_O(A)$ is the desired characteristic polynomial with variables replaced by the transfer matrix $A$
+ $W_O$ is the observability matrix

---
## Reduced-order Observer

Some states of a system are measurable by observing the output, so the observer can only focus on the unmeasurable states. Such state observer is called reduced-order observer. The basic idea of a reduced-order observer makes use of the coupled relation between states, that's using measurable states to estimate the unmeasurable ones.
$$x=\begin{bmatrix}x_a\\x_b\end{bmatrix}$$
+ $x_a$ contains the measurable states
+ $x_b$ contains the unmeasurable states

The original state equation is detected into two equations
$$\begin{bmatrix}x_a(k+1)\\x_b(k+1)\end{bmatrix}=\begin{bmatrix}A_{aa}&A_{ab}\\A_{ba}&A_{bb}\end{bmatrix}\begin{bmatrix}x_a(k)\\x_b(k)\end{bmatrix}+\begin{bmatrix}B_a\\B_b\end{bmatrix}u(k)$$
Notice some variables in the equations are already measurable and known, such as $x_a(k+1), x_a(k), u(k)$
$$\begin{cases}\color{pink}x_a(k+1)\color{black}=A_{aa}\color{pink}x_a(k)\color{black}+A_{ab}x_b(k)+B_a \color{pink}u(k)\color{black}\\x_b(k+1)=A_{ba}\color{pink}x_a(k)\color{black}+A_{bb}x_b(k)+B_b \color{pink}u(k)\color{black}\end{cases}$$
The equations can be treated as a new state space!
$$\begin{cases}x_b(k+1)=\color{red}A_{bb}\color{black}x_b(k)+\color{blue}[A_{ba}x_a(k)+B_b u(k)]\\x_a(k+1)-A_{aa}x_a(k)-B_a u(k)=\color{brown}A_{ab}\color{black}x_b(k)\end{cases} \quad\to\quad \begin{cases}x_b(k+1)=\color{red}A\color{black}x_b(k)+\color{blue}B\color{black}u(k)\\y(k)=\color{brown}C\color{black}x_b(k)\end{cases}$$
The remain stages are the same as full-order observer design

---
## Current Observer

Current Observer estimates state $\hat{x}(k)$ from the output of last instant $y(k)$ and corrects the estimation based on the current output $y(k)$, yielding the final result $\bar{x}(k)$

$$\begin{cases}\hat{x}(k+1)=A\bar{x}(k)+Bu(k)\\\bar{x}(k+1)=\hat{x}(k+1)+L_C[y(k+1)-C\hat{x}(k+1)]\end{cases}$$
Eliminate the intermediate $\hat{x}(k)$ and get
$$\bar{x}(k+1)=(A-L_C CA)\bar{x}(k)+(B-L_CCB)u(k)+L_Cy(k+1)$$
Compared to closed-loop predictive observer, the transfer matrix becomes $A-L_CCA$

### Ackermann’s Formula

Substitute the $C$ with $CA$ in the Ackermann’s Formula used in predictive observer and obtains the formula for current observer design
$$L_C=\alpha_O(A)\begin{bmatrix}CA\\CA^2\\\vdots\\CA^{n}\end{bmatrix}^{-1} \begin{bmatrix}0\\\vdots\\0\\1\end{bmatrix}$$

---
## State Observer Implementation

After the design of state observer, it's connected with the state feedback controller to form a complete functioning system. Since the observer and the controller is in serial, the union of their poles are the poles of the complete system.
$$\alpha(z)=\alpha_C(z)\alpha_O(z)$$
When determining the poles, the $\alpha_C(z)$ is considered for performance and the $\alpha_O(z)$ should have its roots with smaller absolute value (less dominant)


---
## Optimal Control Introduction

The basic optimal control problem is to find a trajectory from the current state $x(i)$ to a desired final state $\xi$ within time interval $[i, N]$, while minimum the cost function $J_i$ 
$$x(k=i) \to x(k=N)=\xi \quad k=i,i+1,\dots,N\quad\quad min(J_i) $$
The state space describing the transition of state $x(k)$ could be nonlinear or even time-variant
$$x(k+1)=f^k(x(k),u(k))$$
The cost function $J_i$ 

### Bellman’s principle of optimality



---
## Discrete-time Linear Quadratic Regulator

For a linear system and a cost function defined by
$$x(k+1)=Ax(k)+Bu(k)$$
$$J_i=\frac{1}{2}x^T(N)S(N)x(N)+\frac{1}{2}\sum_{k=i}^{N-1}(x^T(k)Qx(k)+u^T(k)Ru(k))$$

