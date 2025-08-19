
+ Lec 1 - State Space Basis
	+ [[#1-0 RCL Circuit State Space Model]]
	+ [[#1-1 Simple Mechanic System State Space Model]]
	+ [[#1-2 Servomotor System State Space Model]]
	+ [[#1-3 Output Response of a unit step input]]
	+ [[#1-4 Servomotor Discrete Model]]
	+ [[#1-5 Discrete State Space Poles & Zeros]]
	+ [[#1-6 Derive Pulse Transfer Function]]
	+ [[#1-7 Discrete State Space Poles & Zeros 2]]
	+ [[#1-8 Obtain the closed-form output expression]]
+ Lec 2 - Controllability
	+ [[#2-0 The Similarity Transform of a RCL circuit system]]
	+ [[#2-1 Transform state space to CCF]]
	+ [[#2-2 Canonical forms from transfer function]]
	+ [[#2-3 Transform the OCF system into transfer function]]
	+ [[#2-4 Obtain the state space from the transfer function]]
	+ [[#2-5 Controllability of a circuit system]]
	+ [[#2-6 Controllability of the state space]]
	+ [[#2-7 Input sequence to a goal state]]
	+ [[#2-8 Input sequence to a goal state 2]]
	+ [[#2-9 Controllability of a circuit system 2]]
+ Lec 3 - Observability 
	+ [[#3-1 Observability of a circuit system]]
	+ [[#3-2 Observability of the state space]]
	+ [[#3-3 Find the initial state of a system]]
	+ [[#3-4 Zero-pole cancellation effect]]
	+ [[#3-5 Zero-pole cancellation effect 2]]
	+ [[#3-6 Loss of controllability or observability by sampling]]
	+ [[#3-7 Loss of controllability or observability by sampling 2]]
	+ [[#3-8 Design the state feedback for a discrete system]]
	+ [[#3-9 Closed-loop controllability and observability]]
	+ [[#]]


---
## 1-0  RCL Circuit State Space Model

Build up the state space equation of the RCL circuit for state variables $v_C$ and $i_L$
![[Pasted image 20240923141237.png]]

The state equation is in the form of $\dot{x}(t)=Ax(t)$ since there is no input $u(t)$
$$\begin{bmatrix}\dot{u}_C(t)\\\dot{i}_L(t)\end{bmatrix}=A\begin{bmatrix}{u}_C(t)\\i_L(t)\end{bmatrix}$$
The RCL voltage-current relationship and KVL tells us that
$$Ri_L+\frac{1}{C}\int_0^ti_L(t)+L\frac{di_L(t)}{dt}=0$$
From which we get the desired differential equation
$$\begin{cases}\dot{u}_C(t)=\frac{i_L}{C}\\\dot{i}_L(t)=-\frac{R}{L}i_L-\frac{1}{L}u_C(t)\end{cases}$$
So finally we get
$$\begin{bmatrix}\dot{u}_C(t)\\\dot{i}_L(t)\end{bmatrix}=\begin{bmatrix}0&\frac{1}{C}\\-\frac{1}{L} & -\frac{R}{L}\end{bmatrix}\begin{bmatrix}{u}_C(t)\\i_L(t)\end{bmatrix}$$


---
## 1-1  Simple Mechanic System State Space Model

Build the state space equation of a force-displacement system described by newton's law. The input is force $F(t)$ and output is displacement $x(t)$
$$F=m\ddot{x}(t)$$

Two state variables are required to describe the system. Usually we use displacement $x(t)$ and velocity $v(t)=\dot{x}(t)$ to describe the state.
$$\begin{bmatrix}\dot{x}(t)\\\dot{v}(t)\end{bmatrix}=\begin{bmatrix}0&1\\0 & 0\end{bmatrix}\begin{bmatrix}x(t)\\v(t)\end{bmatrix}+\begin{bmatrix}0\\\frac{1}{m}\end{bmatrix}F$$
$$y(t)=\begin{bmatrix}1&0\end{bmatrix}\begin{bmatrix}x(t)\\v(t)\end{bmatrix}$$

---
## 1-2  Servomotor System State Space Model



---
## 1-3  Output Response of a unit step input

Determine the output response of the following system to a unit step-input $u(t)$ and initial state 
$x(0)=[1\quad -1]^T$
$$\dot{x}(t)=\begin{bmatrix}0 & 1\\0 &-2\end{bmatrix}x(t)+\begin{bmatrix}0\\2\end{bmatrix}u(t)$$
$$y(t)=\begin{bmatrix}1 & 0\end{bmatrix}x(t)$$

First we need to obtain the **state transition matrix** which is an crucial component in the state transition equation.
$$\begin{align}\Phi(t)&=\mathcal{L}^{-1}\{(sI-A)^{-1}\}\\&=\mathcal{L}^{-1}\{\begin{bmatrix}s&-1\\0&s+2\end{bmatrix}^{-1}\}\\&=\mathcal{L}^{-1}\{\begin{bmatrix}\frac{1}{s}&\frac{1}{s(s+2)}\\0&\frac{1}{s+2}\end{bmatrix}\}\\&=\begin{bmatrix}1&\frac{1}{2}-\frac{1}{2}e^{-2t}\\0 &e^{-2t}\end{bmatrix}\end{align}$$
The state transition equation
$$\begin{align}x(t)&=\Phi(t) x(0)+\int_0^t \Phi(t-\tau)Bu(\tau)d\tau\\&=\begin{bmatrix}1&\frac{1}{2}-\frac{1}{2}e^{-2t}\\0 &e^{-2t}\end{bmatrix}\begin{bmatrix}1\\-1\end{bmatrix}+\int_0^t \begin{bmatrix}1&\frac{1}{2}-\frac{1}{2}e^{-2(t-\tau)}\\0 &e^{-2(t-\tau)}\end{bmatrix}\begin{bmatrix}0\\2\end{bmatrix}d\tau\\&=\begin{bmatrix}\frac{1}{2}+\frac{1}{2}e^{-2t}\\-e^{-2t}\end{bmatrix}+\begin{bmatrix}\frac{1}{2}e^{-2t}-\frac{1}{2}+t\\1-e^{-2t}\end{bmatrix}\\&=\begin{bmatrix}t+e^{-2t}\\1-2e^{-2t}\end{bmatrix}\end{align}$$
Then calculate the output $y(t)$
$$y(t)=\begin{bmatrix}1 & 0\end{bmatrix}\begin{bmatrix}t+e^{-2t}\\1-2e^{-2t}\end{bmatrix}=t+e^{-2t}$$

---
## 1-4  Servomotor Discrete Model

A servomotor has a continuous-time state space representation as shown below. Sample the system with a sampling period of $T = 0.1s$ and obtain a discrete-time state space model of the motor.
$$\dot{x}(t)=\begin{bmatrix}0 & 1\\0 &-1\end{bmatrix}x(t)+\begin{bmatrix}0\\1\end{bmatrix}u(t)$$
$$y(t)=\begin{bmatrix}1 & 0\end{bmatrix}x(t)$$

As the discrete state space equation is derived from the continuous time state transition equation, we should derive the state transition matrix $\Phi(t)$ first.
$$\Phi(t)=\mathcal{L}^{-1}\{(sI-A)^{-1}\}=\mathcal{L}^{-1}\{\begin{bmatrix}\frac{1}{s}&\frac{1}{s(s+1)}\\0&\frac{1}{s+1}\end{bmatrix}\}=\begin{bmatrix}1&1-e^{-t}\\0&e^{-t}\end{bmatrix}$$
Then calculate the state transfer and input matrix
$$A'=\Phi(T)=\begin{bmatrix}1&1-e^{-T}\\0&e^{-T}\end{bmatrix}=\begin{bmatrix}1&0.095\\0&0.905\end{bmatrix}$$
$$B'=\int_0^T\Phi(\tau)d\tau B=\begin{bmatrix}T-1+e^{-T}\\1-e^{-T}\end{bmatrix}=\begin{bmatrix}0.00484\\0.095\end{bmatrix}$$
Thus the discrete model is
$$\dot{x}(t)=\begin{bmatrix}1&0.095\\0&0.905\end{bmatrix}x(t)+\begin{bmatrix}0.00484\\0.095\end{bmatrix}u(t)$$
$$y(t)=\begin{bmatrix}1 & 0\end{bmatrix}x(t)$$

---
## 1-5  Discrete State Space Poles & Zeros

Derive the poles and zeros from the given system
$$x(k+1)=\begin{bmatrix}1.35 & 0.55\\-0.45 &0.35\end{bmatrix}x(k)+\begin{bmatrix}0.5\\0.5\end{bmatrix}u(k)$$
$$y(k)=\begin{bmatrix}1 & -1\end{bmatrix}x(k)$$
The equation for poles
$$det(z_pI-A)=z^2_p-1.7z_p+0.72=0$$
The equation for zeros has $z_0$ cancelled out, meaning there's no zero.
$$det\begin{bmatrix}z_0I-A &-B\\C&D\end{bmatrix}=1\neq0$$
So the system have two poles and no zero
$$z_{p1}=0.9\quad\quad z_{p2}=0.8$$

---
## 1-6  Derive Pulse Transfer Function

Convert the given system to Pulse Transfer Function
$$x(k+1)=\begin{bmatrix}0&1\\0&0\end{bmatrix}x(k)+\begin{bmatrix}0\\1\end{bmatrix}u(k)$$
$$y(k)=\begin{bmatrix}1 & 0\end{bmatrix}x(k)$$
The Pulse Transfer Function is given by
$$\begin{align}\frac{Y(z)}{U(z)}&=C(zI-A)^{-1}B+D\\&=\begin{bmatrix}1 & 0\end{bmatrix}\begin{bmatrix}z & -1\\0&z\end{bmatrix}^{-1}\begin{bmatrix}0 \\ 1\end{bmatrix}\\&=\frac{1}{z^2}\end{align}$$

---
## 1-7  Discrete State Space Poles & Zeros 2

Derive the poles and zeros of a system from the given state space matrices 
$$A=\begin{bmatrix}-1 & 0\\0 &-2\end{bmatrix}\quad B=\begin{bmatrix}1\\2\end{bmatrix}\quad C=\begin{bmatrix}-1&1\end{bmatrix}\quad D=0$$
The poles are calculated by
$$det(z_pI-A)=(z_p+1)(z_p+2)=0$$
The zeros are calculated by
$$det\begin{bmatrix}z_0I-A &-B\\C&D\end{bmatrix}=-1\neq0$$
So the system has two poles and no zero
$$z_{p1}=-1\quad\quad z_{p2}=-2$$

---
## 1-8  Obtain the closed-form output expression

Calculate the closed-form output expression for the given system assuming the initial state variable $x(0)=\begin{bmatrix}0&0\end{bmatrix}^T$ and input $u(k)=1$
$$x(k+1)=\begin{bmatrix}0&1\\-2 &-3\end{bmatrix}x(k)+\begin{bmatrix}0\\1\end{bmatrix}u(k)$$
$$y(k)=\begin{bmatrix}3 & 1\end{bmatrix}x(k)$$
The discrete state transition equation
$$x(k)=A^kx(0)+\sum_{i=0}^{k-1}A^{k-1-i}Bu(i)=\sum_{i=0}^{k-1}A^{k-1-i}B$$

---
## 2-0  The Similarity Transform of a RCL circuit system





---
## 2-1  Transform state space to CCF

$$A=\begin{bmatrix}-0.5 & 0\\0 &-0.8\end{bmatrix}\quad B=\begin{bmatrix}1\\1\end{bmatrix}\quad C=\begin{bmatrix}1&-2\end{bmatrix}\quad D=0$$

First we need to check the controllability of the system
$$rank(\begin{bmatrix}B&AB\end{bmatrix})=rank(\begin{bmatrix}1&-0.5\\1&-0.8\end{bmatrix})=2$$
The system is controllable. Then we can obtain the CCF of $A$ from the characteristic polynomial according to the definition
$$|\lambda I-A|=\lambda^2+1.3\lambda+0.4$$
$$A_C=\begin{bmatrix}0&1\\-0.4&-1.3\end{bmatrix} \quad B_C=\begin{bmatrix}0\\1\end{bmatrix}$$
The transform matrix $P$ that converts the system into the CCF form is defined by
$$P=W_C \tilde{W}_C^{-1}=\begin{bmatrix}B&AB\end{bmatrix}\begin{bmatrix}B_C&A_CB_C\end{bmatrix}^{-1}=\begin{bmatrix}1&-0.5\\1&-0.8\end{bmatrix}\begin{bmatrix}0&1\\1&-1.3\end{bmatrix}^{-1}=\begin{bmatrix}0.8 &1\\0.5&1\end{bmatrix}$$
Then the $C,D$ matrix in CCF is calculated by
$$C_C=CP=\begin{bmatrix}-0.2&-1\end{bmatrix} \quad D_C=D$$

---
## 2-2  Canonical forms from transfer function

Convert the following transfer function into CCF state space
$$G(z)=\frac{-2z^3+2z^2-z+2}{z^3+z^2-z-\frac{3}{4}}$$
The CCF state transfer matrix can be directly derived from the denominator polynomial since the pole of the system is defined by the characteristic equation
$$|\lambda I-A|=\lambda^3+\lambda^2-\lambda-\frac{3}{4}$$
$$A_C=\begin{bmatrix}0&1&0\\0&0&1\\\frac{3}{4}&1&-1\end{bmatrix} \quad B_C=\begin{bmatrix}0\\0\\1\end{bmatrix}$$
The output matrix $C_C$ and feed-forward matrix $D$ can be directly written from the original transfer function if the function has its numerator order smaller than the denominator order. So we just need a division here
$$G(z)=\frac{-2z^3+2z^2-z+2}{z^3+z^2-z-\frac{3}{4}}=\frac{4z^2-3z+\frac{1}{2}}{z^3+z^2-z-\frac{3}{4}}-2$$
So we have 
$$C_C=\begin{bmatrix}\frac{1}{2}&-3&4\end{bmatrix}\quad D=-2$$

---
## 2-3  Transform the OCF system into transfer function

$$\begin{align}x(k+1)&=\begin{bmatrix}0&-a_0\\1&-a_1\end{bmatrix}x(k)+\begin{bmatrix}b_0\\b_1\end{bmatrix}u(k)\\y(k)&=\begin{bmatrix}0&1\end{bmatrix}x(k)\end{align}$$

The coefficients of the denominator polynomial can be derived from transfer matrix $A$
$$D(z)=z^2+a_1z+a_0$$
The coefficients of the numerator polynomial can be derived from the OCF input matrix $B$
$$N(z)=b_1z+b_0$$
Then the transfer function is 
$$G(z)=\frac{b_1z+b_0}{z^2+a_1z+a_0}$$

---
## 2-4  Obtain the state space from the transfer function

$$\frac{Y(z)}{U(z)}=\frac{1}{z^2-1.7z+0.72}$$
Firstly, we need to convert the discrete system back to its differential equation form and choose the state variables from it.
$$$$


---
## 2-5  Controllability of a circuit system

![[Pasted image 20241014152228.png]]

---
## 2-6  Controllability of the state space

$$A=\begin{bmatrix}1&0\\0&1\end{bmatrix} \quad B=\begin{bmatrix}1\\1\end{bmatrix}$$

The controllability matrix is
$$W_C=\begin{bmatrix}B&AB\end{bmatrix}=\begin{bmatrix}1&1\\1&1\end{bmatrix}$$
$$rank(W_C)=1$$
So the system is not controllable

---
## 2-7  Input sequence to a goal state

Investigate the controllability of the system and find the input sequence (if it exists) which drives the system to $x(2)=\begin{bmatrix}1\\1.2\end{bmatrix}$ from the origin
$$A=\begin{bmatrix}1&1\\0&1\end{bmatrix} \quad B=\begin{bmatrix}0\\1\end{bmatrix}$$
The controllability matrix is
$$W_C=\begin{bmatrix}B&AB\end{bmatrix}=\begin{bmatrix}0&1\\1&1\end{bmatrix}$$
$$rank(W_C)=2$$
Thus the system is controllable. The state transition equation from $x(0)=\begin{bmatrix}0\\0\end{bmatrix}$ to $x(2)=\begin{bmatrix}1\\1.2\end{bmatrix}$ is given by
$$\begin{align}x(2)&=A[Ax(0)+Bu(0)]+Bu(1)\\&=A^2x(0)+ABu(0)+Bu(1)\\&=\begin{bmatrix}1\\1\end{bmatrix}u(0)+\begin{bmatrix}0\\1\end{bmatrix}u(1)\end{align}$$
Which means
$$\begin{cases}u(0)=1\\u(0)+u(1)=1.2\end{cases}$$
Then
$$u(0)=1 \quad\quad u(1)=0.2$$

---
## 2-8  Input sequence to a goal state 2

Investigate the controllability of the system and find the input sequence (if it exists) which drives the system to $x(3)=\begin{bmatrix}6&-8&2\end{bmatrix}^T$ from the $x(0)=\begin{bmatrix}0&-1&3\end{bmatrix}^T$

$$x(k+1)=\begin{bmatrix}1&2&0\\4&-1&0\\0&1&3\end{bmatrix}x(k)+\begin{bmatrix}-1\\1\\0\end{bmatrix}u(k)$$

The rank of the controllability matrix is full, showing the the system is controllable
$$rank(W_C)=rank(\begin{bmatrix}-1&1&-9\\1&-5&9\\0&1&-2\end{bmatrix})=3$$
Then the state transition equation is
$$\begin{align}x(3)&=A^3x(0)+A^2Bu(0)+ABu(1)+Bu(2)\\&=\begin{bmatrix}-18\\9\\66\end{bmatrix}+\begin{bmatrix}-9\\9\\-2\end{bmatrix}u(0)+\begin{bmatrix}1\\-5\\1\end{bmatrix}u(1)+\begin{bmatrix}-1\\1\\0\end{bmatrix}u(2)\end{align}$$


---
## 2-9  Controllability of a circuit system 2



---
## 3-1  Observability of a circuit system

Check if the system is observable


The state space of the circuit system is written as
$$\begin{bmatrix}\dot{x}_1\\\dot{x}_2\end{bmatrix}=\begin{bmatrix}0&-1\\1&0\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}+\begin{bmatrix}1\\0\end{bmatrix}u(t)$$
$$\begin{bmatrix}y_1\\y_2\end{bmatrix}=\begin{bmatrix}0&0\\1&0\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}+\begin{bmatrix}2\\0\end{bmatrix}u(t)$$

The observability matrix
$$W_O=\begin{bmatrix}C\\CA\end{bmatrix}=\begin{bmatrix}0&0\\1&0\\0&0\\0&-1\end{bmatrix}=2$$

---
## 3-2  Observability of the state space

$$A=\begin{bmatrix}1.1&-0.3\\1&0\end{bmatrix} \quad C=\begin{bmatrix}1&-0.5\end{bmatrix}$$

The rank of the observability matrix
$$rank(W_O)=rank(\begin{bmatrix}C\\CA\end{bmatrix})=rank(\begin{bmatrix}1&-0.5\\0.6&-0.3\end{bmatrix})=2$$
So the system is observable

---
## 3-3  Find the initial state of a system

Inspect the observability of the given system and find the initial state vector $x(0)$ of the system. Assume that $u(0)=u(1)=0, y(0)=1, y(1)=1.2$
$$A=\begin{bmatrix}1&0\\1&1\end{bmatrix} \quad C=\begin{bmatrix}0&1\end{bmatrix}$$
The rank of the observability matrix shows that the system is observable
$$rank(W_O)=rank(\begin{bmatrix}C\\CA\end{bmatrix})=rank(\begin{bmatrix}0&1\\1&1\end{bmatrix})=2$$
The equation regarding the inital state is
$$\begin{cases}y(0)=Cx(0)\\y(1)=C(Ax(0)+Bu(0))+Du(1)\end{cases}$$
Expand the state vector and get
$$\begin{cases}x_2(0)=1\\x_1(0)+x_2(0)=1.2\end{cases}$$
So the result is 
$$x(0)=\begin{bmatrix}0.2\\1\end{bmatrix}$$

---
## 3-4  Zero-pole cancellation effect

Check the controllability and observability of the following system with a pole cancelled by a zero
$$\frac{Y(z)}{U(z)}=\frac{z+0.2}{z^2+z+0.16}=\frac{z+0.2}{(z+0.8)(z+0.2)}$$




---
## 3-5  Zero-pole cancellation effect 2



---
## 3-6  Loss of controllability or observability by sampling


---
## 3-7  Loss of controllability or observability by sampling 2



---
## 3-8  Design the state feedback for a discrete system

Determine a state feedback gain matrix $K$ for the given servo system such that the closed-loop poles are at $0.888\pm j0.173$
$$x(k+1)=\begin{bmatrix}1&0.0952\\0&0.905\end{bmatrix}x(k)+\begin{bmatrix}0.00484\\0.0952\end{bmatrix}u(k)$$
$$y(k)=\begin{bmatrix}1&0\end{bmatrix}x(k)$$

Firstly, check the controllability of the system to ensure that the poles can be placed on arbitrary position.
$$rank(W_C)=rank(\begin{bmatrix}B&AB\end{bmatrix})=rank(\begin{bmatrix}0.00484&0.0139\\0.0952&0.0862\end{bmatrix})=2$$
The equation of $K$ can be established by equating the state close-looped feedback characteristic polynomial and the desired polynomial ($K$ is a 1x2 matrix)
$$\det(zI-A+BK)=(z-0.888-j0.173)(z-0.888+j0.173)$$
In matrix form
$$\begin{bmatrix}z&0\\0&z\end{bmatrix}-\begin{bmatrix}1&0.0952\\0&0.905\end{bmatrix}+\begin{bmatrix}0.00484k_1&0.00484k_2\\0.0952k_1&0.0952k_2\end{bmatrix}=z^2-1.776z+0.818$$
We get
$$k_1=\quad\quad k_2=$$

---
## 3-9  Closed-loop controllability and observability



---
## 3-10  



---
## 3-11  Using Ackermann's Formula on space feedback design

Retry example 3-8 using Ackmann's Formula
(The desired characteristic polynomial $\alpha_C(z)=z^2-1.776z+0.819$)

$$x(k+1)=\begin{bmatrix}1&0.0952\\0&0.905\end{bmatrix}x(k)+\begin{bmatrix}0.00484\\0.0952\end{bmatrix}u(k)$$
$$y(k)=\begin{bmatrix}1&0\end{bmatrix}x(k)$$
The second order Ackmann's formula 
$$\begin{align}K&=\begin{bmatrix}0&1\end{bmatrix}W_C^{-1}\alpha_C(A)\\&=\begin{bmatrix}0&1\end{bmatrix}\begin{bmatrix}B&AB\end{bmatrix}^{-1}(A^2-1.776A+0.819I)\end{align}$$

---
## 3-12  



---
## 4-1  Closed-loop Observer Design

$$\begin{cases}x(k+1)=\begin{bmatrix}1&T\\0&1\end{bmatrix}x(k)+\begin{bmatrix}\frac{T^2}{2}\\T\end{bmatrix}u(k)\\y(k)=\begin{bmatrix}1&0\end{bmatrix}x(k)\end{cases}$$

Design an observer for the above plant so that the observer poles are $z_{1,2}=0.4\pm j0.4$ and the measurement is $x_1(k)$

The transfer matrix of the closed-loop system is $A-L_o C$, so the chracteristic polynomial can be calculated by
$$\begin{vmatrix}zI-(A-L_oC)\end{vmatrix}=\det(\begin{bmatrix}z&0\\0&z\end{bmatrix}-\begin{bmatrix}1&T\\0&1\end{bmatrix}+\begin{bmatrix}l_1\\l_2\end{bmatrix}\begin{bmatrix}1&0\end{bmatrix})=z^2+(l_1-2)z+1-l_1+l_2T$$
Equate two chracteristic polynomials together
$$\begin{align}z^2+(l_1-2)z+1-l_1+l_2T&=(z-0.4-j0.4)(z-0.4+j0.4)\\&=z^2-0.8z+0.32\end{align}$$
Finally we have
$$\begin{cases}l_1=1.2\\l_2=\frac{0.52}{T}\end{cases}$$

---
## 4-2



---
## 