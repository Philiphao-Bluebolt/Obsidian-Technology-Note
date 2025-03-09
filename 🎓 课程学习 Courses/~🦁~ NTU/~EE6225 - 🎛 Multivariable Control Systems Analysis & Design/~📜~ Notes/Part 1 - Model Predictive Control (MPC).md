+ **Goal** - find a **optimal** control balancing control signal fluctuation and output square error

Model Predictive Control is a model-based control method that uses the **control model** of the controlled plant system to predict future outputs and then generates the **optimal** control signal based on the prediction.

The core of MPC is to solve the following optimization problem and use the optimal solution as the control input signal

+ **Objective Function**
$$\min_{\Delta u_i} J=\sum_{i=N_1}^{N_2}[\hat{y}(k+i|k)-\hat{w}(k+i|k)]^2+\lambda\sum_{i=0}^{N_u}[\Delta \hat u(k+i|k)]^2$$
+ **Optimal Solution**
$$\hat{U}=(G^TG+\lambda I)^{-1}G^T(\hat{W}-F)$$
+ **Next Input**
$$u(k)=k_1w(k)+k_2x(k)+k_3 u(k-1)$$

+ **Mathematics Model**
	+ [[#Principle and Standard Form]]
		+ [[#Model]]
		+ [[#Prediction]]
		+ [[#Control]]
	+ [[#General Form of State Space]]
		+ [[#Integration Action]]
		+ [[#Feed-Forward]]
+ **Parameter Tuning**
	+ [[#Control System with MPC]]
	+ [[#Parameter Effects]]
	+ [[#Extreme Cases]]
+ **Constraints**
	+ [[#Standard Form of Constraints]]
	+ [[#Constraint Optimal Solution]]
+ **State Estimation**

+ **Examples**
	+ [[#Ex 1 - Swimming Pool Temperature Control]]


(In this tutorial, we use the hat to represent future values, for example $\hat{y}(k+1|k)$)

---
## Principle and Standard Form

MPC requires the following parts to work

1. **Plant Model** - the state space **model** of the plant (controlled system) for **prediction**
2. **Objective Function** - deciding how far the prediction and control reaches and their trade-off

### Model

Assume we have built a discretized state space model $\Sigma(A_p,B_p,C_p,D_p)$ for the plant (the index $p$ stands for prediction here)
$$\begin{cases}x(k+1)=A_px(k)+B_pu(k)\\y(k)=C_px(k)\end{cases}$$
We can easily derive the output **transition equation** from the model. 

$$\begin{align}y(k+1)&=C_p[A_px(k)+B_pu(k)]\\y(k+2)&=C_p[A_p^2x(k)+A_pB_pu(k)+B_pu(k+1)]\\y(k+3)&=C_p[A_p^3x(k)+A_p^2B_pu(k)+A_pB_pu(k+1)+B_pu(k+2)]\\&\vdots\\y(k+i)&=C_p[A_p^ix(k)+\sum^i_{j=1}A_p^{i-j}B_pu(k+j-1)]\\&\vdots\\y(k+N)&=C_p[A_p^Nx(k)+\sum^N_{j=1}A_p^{N-j}B_pu(k+j-1)]\end{align}$$

The equation will be used in the prediction stage. 
$$y(k+i)=\color{red}C_pA_p^i\color{black}x(k)+\color{green}\sum^i_{j=1}C_pA_p^{i-j}B_p\color{black}u(k+j-1)$$
### Prediction

The prediction of possible future outputs $\hat y(k+i|k)$ is obtained using the transition equation. Firstly, we rewrite the equation in the matrix form.

$$\begin{bmatrix}\hat y(k+1)\\\hat y(k+2)\\\vdots\\\hat y(k+N)\end{bmatrix}=\color{red}\begin{bmatrix}C_pA_p\\C_pA_p^2\\\vdots\\C_pA_p^N\end{bmatrix}\color{black}x(k)+\color{green}\begin{bmatrix}B_p&0&\cdots&0\\A_pB_p&B_p&\cdots&0\\\vdots&\vdots&\ddots&0\\A^N_pB_p&A^{N-1}_pB_p&\cdots&B_p\end{bmatrix}\color{black}\begin{bmatrix}\hat u(k)\\\hat u(k+1)\\\vdots\\\hat u(k+N-1)\end{bmatrix}$$

We're more interested in the **fluctuation** of the control signal then its actual value. So the control inputs are represented as the increments instead: $\hat{u}(k+i)=\hat{u}(k+i-1)+\Delta \hat{u}(k+i)$

$$\begin{bmatrix}\hat u(k)\\\hat u(k+1)\\\vdots\\\hat u(k+N-1)\end{bmatrix}=\begin{bmatrix}1\\1\\\vdots\\1\end{bmatrix}u(k-1)+\begin{bmatrix}1&0&\cdots&0\\1&1&\cdots&0\\\vdots&\vdots&\ddots&0\\1&1&\cdots&1\end{bmatrix}\begin{bmatrix}\Delta \hat u(k)\\\Delta \hat u(k+1)\\\vdots\\\Delta \hat u(k+N-1)\end{bmatrix}$$

Combined the two matrix equations and we get the **output prediction** equation

$$\hat{Y}=\color{red}\Phi\color{black} x(k)+\color{orange}\Gamma \color{black}u(k-1)+\color{blue}\mathrm{G}\color{black}\hat{U}=F+\color{blue}\mathrm{G}\color{black}\hat{U}$$

$$\begin{bmatrix}\hat y(k+1)\\\hat y(k+2)\\\vdots\\\hat y(k+N)\end{bmatrix}=\color{red}\begin{bmatrix}C_pA_p\\C_pA_p^2\\\vdots\\C_pA_p^N\end{bmatrix}\color{black}x(k)+\color{orange}\begin{bmatrix}B_p\\A_pB_p+B_p\\\vdots\\\sum^N_{j=1}A_p^{N-j}B_p\end{bmatrix}\color{black} u(k-1)+\color{blue}\begin{bmatrix}B_p&0&\cdots&0\\A_pB_p+B_p&B_p&\cdots&0\\\vdots&\ddots&\ddots&\vdots\\\sum^N_{j=1}A_p^{N-j}B_p&\cdots&\cdots&B_p\end{bmatrix}\color{black}\begin{matrix}\end{matrix}\begin{bmatrix}\Delta \hat u(k)\\\Delta \hat u(k+1)\\\vdots\\\Delta \hat u(k+N-1)\end{bmatrix}$$

The equation implies that the future outputs of the system is determined by two types of information represented by two vectors respectively:

1. **The Past Vector** $F$  - contains $u(k-1)$ and $x(k)$, can not be changed 
2. **The Future Vector** $\hat{U}$ - can be changed

The past state and inputs can not be changed. It's the **future** inputs that we can control to reach our goal.

> [!QUESTION] Should we add a estimation hat sign $\hat{\quad}$ to the denotation of the past vector $F$? 
> 


### Control

When applying the MPC control, we wish to achieve two goals

+ **Minimize Following Error** - the output $y$ should be the same as the reference $w$
+ **Minimize Control Fluctuation** - the control input $u$ should not changed too aggressively

Those targets can be formatted into a objective function $J$ with four parameters
$$J=\sum_{i=N_1}^{N_2}[\color{MediumOrchid}\hat{y}(k+i|k)\color{black}-\color{SteelBlue}\hat{w}(k+i|k)\color{black}]^2+\lambda\sum_{i=0}^{N_u}[\color{DarkGoldenrod}\Delta \hat u(k+i|k)\color{black}]^2$$
+ **Prediction Lower Horizon** $N_1$
+ **Prediction Upper Horizon** $N_2$
+ **Control Horizon** $N_u$
+ **Control Fluctuation Ratio** $\lambda$

The objective function $J$ can be written in matrix form in which the sum of squares is represented as a vector's self inner product

$$J=(\color{MediumOrchid}\hat{Y}\color{black}-\color{SteelBlue}\hat{W}\color{black})^T(\color{MediumOrchid}\hat{Y}\color{black}-\color{SteelBlue}\hat{W}\color{black})+\lambda \color{DarkGoldenrod}\hat{U}\color{black}^T\color{DarkGoldenrod}\hat{U}\color{black}$$

$$\color{MediumOrchid}\hat{Y}=\begin{bmatrix}\hat{y}(k+N_1)\\\hat{y}(k+N_1+1)\\\vdots\\\hat{y}(k+N_2)\end{bmatrix}\color{black}\quad\quad \color{SteelBlue}\hat{W}=\begin{bmatrix}\hat{w}(k+N_1)\\\hat{w}(k+N_1+1)\\\vdots\\\hat{w}(k+N_2)\end{bmatrix}\color{black}\quad\quad\color{DarkGoldenrod} \hat{U}=\begin{bmatrix}\Delta \hat{u}(k)\\\Delta\hat{u}(k+1)\\\vdots\\\Delta\hat{u}(k+N_u)\end{bmatrix}\color{black}$$

As we have derived the prediction equation $\hat{Y}=F+G\hat{U}$, the future outputs $\hat y$ can be represented by the future control inputs $\Delta \hat{u}$
$$J=(\hat{Y}^T-\hat{W}^T)(\hat{Y}-\hat{W})+\lambda \hat{U}^T\hat{U}$$

> [!QUESTION]  The control increment vector $\hat{U}$ in the objective function $J$ and the  control increment vector used to replace $\hat{Y}$ has different element index range. How can they combine?
> $$\hat{U}_u=\begin{bmatrix}\Delta \hat{u}(k)\\\Delta\hat{u}(k+1)\\\vdots\\\Delta\hat{u}(k+N_u)\end{bmatrix}\quad \hat{U}_p=\begin{bmatrix}\Delta \hat{u}(k+N_1-1)\\\Delta\hat{u}(N_1+1)\\\vdots\\\Delta\hat{u}(k+N_2-1)\end{bmatrix}$$


---
## General Form of State Space

+ **Characteristics** - increment $\Delta \hat{u}$ as input instead of $\hat{u}$

We can use the control input increment $\Delta u(k)$ instead of $u(k)$ in the state space representative of the plant.


### Integration Action


### Feed-Forward




---
## Control System with MPC 

MPC 




---
## Parameter Effects

The parameters of a MPC control system includes the controller parameters and the extrinsic parameters.






### 



---
## Extreme Cases

Here're special cases when some of the parameters in MPC control are set to **zero** or **infinity**

| Parameters                | Feedback-off |   Mean-level    |   Deadbeat   | (Not so) Perfect |
| ------------------------- | :----------: | :-------------: | :----------: | :--------------: |
| **Lower Horizon** $N_1$   |      /       |                 |   $N_1=n$    |     $N_1=1$      |
| **Upper Horizon** $N_2$   |      /       | $N_2\to \infty$ | $N_2\geq 2n$ |     $N_2=1$      |
| **Control Horizon** $N_u$ |      /       |                 |   $N_u=n$    |     $N_u=1$      |
| **Output Weight** $Q(i)$  |   $Q(i)=0$   |  $Q(i)>>R(i)$   | $Q(i)>>R(i)$ |   $Q(i)>>R(i)$   |
| **Control Weight** $R(i)$ | $R(i)>>Q(i)$ |    $R(i)=0$     |   $R(i)=0$   |     $R(i)=0$     |

### Feedback-off



### Mean-level



### Deadbeat



### (Not so) Perfect




---
## Standard Form of Constraints

In real scenerio, constraints exist in every part of the control system and they greatly affect the performance of MPC. The most common constraints include

+ **Input Increment Constraint** - $\Delta u_\min<\Delta\hat{u}(k+i|k)<\Delta u_\max$
+ **Input Constraint** - $u_\min<\hat{u}(k+i|k)<u_\max$
+ **Output Constraint** - $y_\min<\hat{y}(k+i|k)<y_\max$

All of those constraints inequalities can be transformed to the **standard form** in which they are represented by the **input increment** vector $\hat{U}$
$$\Omega \hat{U}<\omega$$

+ **Input Increment Constraint**
$$$$




---
## Constraint Optimal Solution 




---
## Ex 1 - Swimming Pool Temperature


---
## Ex 2 - Water Heater


---
## Ex 3 - Constraints Standardization





