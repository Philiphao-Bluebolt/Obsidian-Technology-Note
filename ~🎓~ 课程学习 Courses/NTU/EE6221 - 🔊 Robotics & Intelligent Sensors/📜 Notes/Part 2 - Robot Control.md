+ **Goal** - Design a controller, specific motor forces and torques to obtain desired robot motion

While the desired robot motion is usually given by end effector position and orientation, the robot joints only output forces and torques, which are derivatives of velocities and positions. As a result, a control system is required.
![[Pasted image 20241118142109.png]]

To guarantee a high accuracy in the control, nonlinear control methods are used.

+ [[#Prerequisite]]
	+ [[#Control Law Partitioning]]
	+ [[#Lagrangian Mechanics]]
+ [[#Robot Dynamic Model]]


+ [[#Example]]


---
## Prerequisite 

There're some prerequisite for robot controller design.

### Control Law Partitioning



### Lagrangian Mechanics

Lagrangian mechanics provides a special calculation system of classcial mechanics based on energy and degree of freedom. It's a convenient approach to analysis conservative mechanic system.

Assume a system with $n$ degrees of freedom.

#### Legrangian Function

The Legrangian function of the system is defined by the difference of kinematic and potential energy in the system, it's the function of $n$ (either linear or angular) velocities and positions

$$L=E_k-E_p$$

+ $E_k$ is the total kinematic energy, a function of velocities $\dot{\theta_1},\dot{\theta_2},...,\dot{\theta_n}$
+ $E_p$ is the total potential energy, a function of positions $\theta_1,\theta_2,...,\theta_n$

#### Lagrange's equation

Lagrange's equation is an equivalence to the Newton's second law, it



---
## Robot Dynamic Model





---
## Example - PD Controller Design

Consider the dynamic equation of the 2-link polar robot with mass $m = 2\mathrm{kg}$. Design a PD Computed torque controller for the robot. The resonance frequency of the robot is $12\mathrm{rad/s}$

