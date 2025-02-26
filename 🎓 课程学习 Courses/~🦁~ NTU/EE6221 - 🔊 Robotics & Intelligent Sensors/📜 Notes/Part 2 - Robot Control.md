+ **Goal** - Design a controller, specific motor forces and torques to obtain desired robot motion

While the desired robot motion is usually given by end effector position and orientation, the robot joints only output forces and torques, which are derivatives of velocities and positions. As a result, a control system is required.
![[Pasted image 20241118142109.png]]

To guarantee a high accuracy in the control, nonlinear control methods are used.

+ [[#Robot Dynamic Model]]
	+ [[#Lagrangian Mechanics]]
		+ [[#Legrangian]]
		+ [[#Lagrange's equation]]
	+ [[#Model Equation]]
+ [[#Position Controller Design]]
	+ [[#Control Law Partitioning]]
	+ [[#PD Controller]]
	+ [[#PID Controller]]
	+ [[#Performance Requirement]]
+ [[#Force Control]]
	+ [[#Force-only Control]]
	+ [[#Hybrid Position-force Control]]
+ [[#Example]]
	+ [[#Single-joint Robot Model]]
	+ [[#Two-joint Robot Model (Revolution + Translation)]]
	+ [[#PD Controller Design]]
	+ [[#Hybrid Position Force Control of a 2 DoF Robot]]


---
## Robot Dynamic Model

+ **Goal** - Get the relationship of the input (torque) and output (position) of the robot joints

### Lagrangian Mechanics

Lagrangian mechanics provides a special calculation system of classcial mechanics based on energy and degree of freedom. It's a convenient approach to analysis conservative mechanic system.

Assume a system with $n$ degrees of freedom.

#### Legrangian

The Legrangian of the system is a function defined by the difference of kinematic and potential energy in the system, it's the function of $n$ (either linear or angular) velocities and positions

$$L=E_k-E_p$$

+ $E_k$ is the total kinematic energy, a function of velocities $\dot{\theta_1},\dot{\theta_2},...,\dot{\theta_n}$
+ $E_p$ is the total potential energy, a function of positions $\theta_1,\theta_2,...,\theta_n$

#### Lagrange's equation

Lagrange's equation is an equivalence to the Newton's second law, it describes the force or torque of the mechanic system with partial derivatives of Legrangian over its velocity and position  variables
$$\frac{d}{dt}\frac{\partial L}{\partial \dot{\theta}}=\tau+\frac{\partial L}{\partial \theta}$$
If the system has more than one degree of freedom, the equation should be written as matrix form
$$\frac{d}{dt}\begin{bmatrix}\frac{\partial L}{\partial \dot{\theta_1}}\\\frac{\partial L}{\partial \dot{\theta_2}}\\\vdots\\\frac{\partial L}{\partial \dot{\theta_n}}\end{bmatrix}=\begin{bmatrix}\tau_1\\\tau_2\\\vdots\\\tau_n\end{bmatrix}+\begin{bmatrix}\frac{\partial L}{\partial \theta_1}\\\frac{\partial L}{\partial \theta_2}\\\vdots\\\frac{\partial L}{\partial \theta_n}\end{bmatrix}$$

### Model Equation

A robot dynamic model establishes the relationship the forces and torques of a degree of freedom and the positions and velocities of a system. It can be derived from the Lagrange equation

$$\frac{d}{dt}\frac{\partial L}{\partial \dot{\theta}}-\frac{\partial L}{\partial \theta}=\tau \quad \to\quad M(\theta)\ddot{\theta}+C(\theta,\dot{\theta})\dot{\theta}+g(\theta)=\tau$$
+ $M(\theta)$ - manipulator mass matrix (always invertible)
+ $C(\theta, \dot{\theta}) \dot{\theta}$ - vector of velocity terms (matrix $C$ is not always detechable)
+ $g(\theta)$ - vector of gravity terms
+ $\theta$ - vector of $n$ joint position (output)
+ $\tau$ - vector of $n$ joint torque (input)

Stages to build up the model

1. Calculate kinematic energy $E_k$ and potential energy $E_p$ of the system respectively
2. Calculate Lagrangian $L$
3. Calculate the Lagrangian equation (in matrix form)

The model is highly nonlinear.

---
## Position Controller Design

+ **Goal** - Design a control law for the nonlinear robot model to achieve desired performance

The robot model is a nonlinear second-order differential equation which is difficult to control. However, it's possible to cancel out the nonlinearity by a method called Control Law Partitioning.

Notice that the torque(force) is the input of the robot joints but also the output of the controller.

### Control Law Partitioning

Control Law aims to seperate the controller into a model-based mapping and a servo portion. The model-based mapping will cancel out the nonlinearity.
$$\tau=\alpha v+\beta$$

+ Substitute the controller output torque vector $\tau$ with $v$ using the model-based mapping 
$$M(\theta)\ddot{\theta}+C(\theta,\dot{\theta})\dot{\theta}+g(\theta)=\alpha v+\beta$$
+ Make the following definition
$$\alpha=M(\theta)$$
$$\beta=C(\theta,\dot{\theta})\dot{\theta}+g(\theta)$$
$$v=\ddot{\theta}$$
The rest work is to design a controller calculating acceleration vector $v$ from the actual $\theta, \dot{\theta}$ and reference input $\theta_d, \dot{\theta}_d,\ddot{\theta}_d$, which is a pure linear process. 

### PD Controller

When using a PD controller, the error equation can be written as
$$v=\ddot{\theta_d}+K_v \dot{E}+K_p E$$
+ $K_v$ - derivative control coefficient matrix ($n\times n$ and **diagonal**)
+ $K_p$ - proportional control coefficient matrix ($n\times n$ and **diagonal**)
+ $E$ - error vector ($n\times 1$), $E=\theta_d-\theta$, $\dot{E}=\dot{\theta_d}-\dot{\theta}$, $\ddot{E}=\ddot{\theta_d}-\ddot{\theta}$

Move the $v$ to right-hand side and get
$$\ddot{E}+K_v \dot{E}+K_p E=0$$

### PID Controller

When using a PID controller, the error equation includes an extra integrator compared to PD
$$v=\ddot{\theta_d}+K_v \dot{E}+K_p E +K_i\int E dt$$
The zero right-hand side form
$$\ddot{E}+K_v \dot{E}+K_p E+K_i\int E dt=0$$
### Performance Requirement

Since the servo controller portion is second-ordered, it can be described by a damping ratio $\xi$
and a undamped natural frequency $\omega_n$ like a standard second order system
$$s^2+2\xi\omega_n s +\omega_n^2$$
There're two universal requirements for the robot controller

+ Oscillation Avoidance - the system should **not** be underdamped
$$\xi\geq 1$$
+ Structural Resonation Avoidance
$$\omega_n\leq 0.5\omega_{res}$$

---
## Force Control

Force control is significant for safety when robot is making contact with the objects.

### Force-only Control

Assume the end effector points at a plane and makes contact vertically. The differetial equation can be derived using Newton's second law
$$m\ddot{x}+f=\tau$$
+ $f$ - contact force modelled as a linear spring $f=K_e(x-x_e)$. It's the **desired** output of force control

The control law partitioning can still be used here
$$m\ddot{x}+f=\tau=\alpha v+\beta$$
Since $\ddot{f}=K_e\ddot{x}$, the PD error control law can be substituted as
$$v=\frac{1}{K_e}(\ddot{f_d}+K_v\dot{e}_f+K_p e_f)$$
The error and derivative of error $\dot{e}_f, e_f$ can be obtained by the contact force spring model equation
$$e_f=k_e(x-x_e)$$
$$\dot{e}_f=k_e\dot{x}$$

### Hybrid Position-force Control

When a multi-joint robot is working, both the position and contact force should be controlled. Hybrid controller is capable of controlling the position of some joints and the contact force of the others.

While designing a hybrid controller, we will apply the control law partitioning for all joints  together and design servo control seperately according to the controlling requirement of a specific joint.

---
## Example 

### Single-joint Robot Model

The robot is connected to the floor through a revolute joint and there's a light-weight link with length $l$ connecting the joint and a load with mass $m$. The joint revolute angle is $\theta$. Derive the Lagrangian equation. 
![[Pasted image 20241119133953.png]]

+ Step 1 - kinematic and potential energy

The kinematic energy is yielded by the revolution of mass around the joint and the potential energy is the gravitational potential energy of the mass

$$E_k=\frac{1}{2}mv^2=\frac{1}{2}ml^2\dot{\theta}^2$$
$$E_p=mgl\sin\theta$$

+ Step 2 - Lagrangian
$$L=E_k-E_p=\frac{1}{2}ml^2\dot{\theta}^2-mgl\sin\theta$$
+ Step 3 - Lagrangian equation
$$\frac{d}{dt}\frac{\partial L}{\partial \dot{\theta}}-\frac{\partial L}{\partial \theta}=ml^2\dot{\theta}+mgl\cos\theta=\tau$$

### Two-joint Robot Model (Revolution + Translation) 

The robot is connected to the floor through a revolute joint and there is a prismatic joint on the link, making the link length $l$ changable. The load fixed at the other end of the link has mass $m$

![[Pasted image 20241119230710.png]]

+ Step 1 - kinematic and potential energy

Now the kinematic energy has two part, revolution by the first joint and translation by the second joint. The potential energy is still gravitational.
$$E_k=\frac{1}{2}ml^2\dot{\theta_1}^2+\frac{1}{2}m\dot{l}^2$$
$$E_p=mgl\sin\theta_1$$
+ Step 2 - Lagrangian
$$L=E_k-E_p=\frac{1}{2}ml^2\dot{\theta_1}^2+\frac{1}{2}m\dot{l}^2-mgl\sin\theta_1$$
+ Step 3 - Lagrangian equation

Because we have two joints here, we need to use matrix form seperating different joints.
$$\begin{align}\frac{d}{dt}\frac{\partial L}{\partial \dot{\theta}}-\frac{\partial L}{\partial \theta}&=\tau\\\frac{d}{dt}\begin{bmatrix} \frac{\partial L}{\partial \dot{\theta_1}}\\\frac{\partial L}{\partial \dot{l}}\end{bmatrix}-\begin{bmatrix} \frac{\partial L}{\partial\theta_1}\\\frac{\partial L}{\partial l}\end{bmatrix}&=\begin{bmatrix} \tau_1\\\tau_2\end{bmatrix}\\\begin{bmatrix}2l\dot{l}m\dot{\theta_1}+ml^2\ddot{\theta_1}\\m\ddot{l}\end{bmatrix}-\begin{bmatrix}-mgl\cos\theta_1\\ml\dot{\theta_1}^2-mg\sin\theta_1\end{bmatrix}&=\begin{bmatrix}\tau_1\\\tau_2\end{bmatrix}\end{align}$$
The final results can be written as
$$\begin{align}M(\theta)\ddot{\theta}+C(\theta,\dot{\theta})\dot{\theta}+g(\theta)&=\tau\\\begin{bmatrix}ml^2&0\\0&m\end{bmatrix}\begin{bmatrix}\ddot{\theta_1}\\\ddot{l}\end{bmatrix}+\begin{bmatrix}2l\dot{l}m\dot{\theta_1}\\-ml\dot{\theta_1}^2\end{bmatrix}+\begin{bmatrix}mgl\cos\theta_1\\mg\sin\theta_1\end{bmatrix}&=\begin{bmatrix}\tau_1\\\tau_2\end{bmatrix}\end{align}$$

### PD Controller Design

Consider the dynamic equation of the 2-joint robot in the last question with mass $m = 2\mathrm{kg}$. Design a PD Computed torque controller for the robot. The resonance frequency of the robot is $12\mathrm{rad/s}$

+ Control Law Partitioning $\tau=\alpha v+\beta$

$$\alpha=M(\theta)=\begin{bmatrix}2l^2&0\\0&2\end{bmatrix}$$
$$\beta=C(\theta,\dot{\theta})\dot{\theta}+g(\theta)=\begin{bmatrix}4l\dot{l}\dot{\theta}_1+19.6l\cos\theta_1\\-2l\dot{\theta}^2_1+19.6\sin\theta_1\end{bmatrix}$$
+ Use PD control
$$v=\ddot{\theta}+K_v\dot{E}+K_p E$$
The equation can be decoupled as
$$v_1=\ddot{\theta}_1+K_{v1}\dot{e}_1+K_{p1}e_1$$
$$v_2=\ddot{l}+K_{v2}\dot{e}_2+K_{p2}e_2$$
Since the two equations are identical in forms, the two pairs of $K_v, K_p$ parameters can be set as identical. Transform the error control differential equation into laplace form
$$\ddot{e}+K_v \dot{e}+K_{p}e\to s^2+2\omega_n\xi s+\omega_n^2$$
The performance requirement should be met. Choose the critical value for better settling time performance.
$$\xi\geq 1\quad\to \quad\xi=1$$
$$\omega_n\leq0.5\omega_{res}=6\mathrm{rad/s}\quad\to\quad \omega_n=6$$

Then calculate $K_v, K_p$
$$K_v=2\omega_n \xi=12$$
$$K_p=\omega_n^2=36$$
Then the whole controller can be described as
$$v=\ddot{\theta}+\begin{bmatrix}12&0\\0&12\end{bmatrix}\dot{E}+\begin{bmatrix}36&0\\0&36\end{bmatrix}E$$
$$\tau = \begin{bmatrix}2l^2&0\\0&2\end{bmatrix}v+\begin{bmatrix}4l\dot{l}\dot{\theta}_1+19.6l\cos\theta_1\\-2l\dot{\theta}^2_1+19.6\sin\theta_1\end{bmatrix}$$

### Hybrid Position Force Control of a 2 DoF Robot

Assume there's a 2-joint robot which can move horizontally and vertically. The dynamic model of the robot is given as the following equations. Design a hybrid controller for both force control on the $x$ axis and motion control on the $y$ axis 
$$\begin{cases}m_1\ddot{x}+f=\tau_1\\(m_1+m_2)\ddot{y}+(m_1+m_2)g=\tau_2\end{cases}$$
Rewrite the dynamic equation in matrix form
$$\begin{bmatrix}m_1&0\\0&m_1+m_2\end{bmatrix}\begin{bmatrix}\ddot{x}\\\ddot{y}\end{bmatrix}+\begin{bmatrix}0\\m_1g+m_2g\end{bmatrix}+\begin{bmatrix}f\\0\end{bmatrix}=\begin{bmatrix}\tau_1\\\tau_2\end{bmatrix}$$
Apply control law partitioning on the matrix equation
$$\alpha=\begin{bmatrix}m_1&0\\0&m_1+m_2\end{bmatrix}$$
$$\beta=\begin{bmatrix}f\\m_1g+m_2g\end{bmatrix}$$
$$v=\begin{bmatrix}\ddot{x}\\\ddot{y}\end{bmatrix}$$
Design the servo control of force ad motion seperately. For exmaple, use PD control here

+ Position Control - $y$
$$\ddot{y}=\ddot{y}_d+k_v\dot{e}_y+k_p e_y$$
+ Force Control - $f$
$$\ddot{x}=\frac{1}{k_e}(\ddot{f}_d+k_v\dot{e}_f+k_pe_f)$$
