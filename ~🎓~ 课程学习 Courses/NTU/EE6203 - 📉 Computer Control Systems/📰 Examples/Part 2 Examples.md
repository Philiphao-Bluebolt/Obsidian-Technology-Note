
---
## State Space Basis

### 1-0  RCL Circuit State Space Model

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

### 1-1  Simple Mechanic System State Space Model

Build the state space equation of a force-displacement system described by newton's law. The input is force $F(t)$ and output is displacement $x(t)$
$$F=m\ddot{x}(t)$$

Two state variables are required to describe the system. Usually we use displacement $x(t)$ and velocity $v(t)=\dot{x}(t)$ to describe the state.
$$\begin{bmatrix}\dot{x}(t)\\\dot{v}(t)\end{bmatrix}=\begin{bmatrix}0&1\\0 & 0\end{bmatrix}\begin{bmatrix}x(t)\\v(t)\end{bmatrix}+\begin{bmatrix}0\\\frac{1}{m}\end{bmatrix}F$$
$$y(t)=\begin{bmatrix}1&0\end{bmatrix}\begin{bmatrix}x(t)\\v(t)\end{bmatrix}$$

### 1-2  Servomotor System State Space Model


### 1-3  Output Response of a unit step input

Determine the output response of the following system to a unit step-input $u(t)$ and initial state 
$x(0)=[1\quad -1]^T$
$$\dot{x}(t)=\begin{bmatrix}0 & 1\\0 &-2\end{bmatrix}x(t)+\begin{bmatrix}0\\2\end{bmatrix}u(t)$$
$$y(t)=\begin{bmatrix}1 & 0\end{bmatrix}x(t)$$

