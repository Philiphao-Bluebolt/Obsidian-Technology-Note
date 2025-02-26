+ **Common Locomotion** - Wheels

Robots uses different equipments to move around but wheels are the most popular choice. In the nature, no animal develops wheels during the evoluation as wheel doesn't work well on rocky and steep terrains. However, rolling is the most efficient approach for locomotion on flat surface.

+ [[#Introduction to Wheels]]
	+ [[#Type of Wheels]]
	+ [[#Configuration on Robots]]
+ [[#Wheeled Robot Forward Kinematics]]
	+ [[#Coordinate Transform]]
	+ [[#Wheel Constraint]]
+ [[#Wheel Kinematic Models]]
	+ [[#Standard Wheel (Fixed or Steered)]]
	+ [[#Castor Wheel]]
	+ [[#Sweden Wheel]]
+ [[#Examples]]
	+ [[#Differential Standard Wheels Driven]]

---
## Introduction to Wheels

Wheels have different types and configuration models when installed on the robots. 

### Type of Wheels

+ **Standard** - rotational axis fixed 
+ **Castor (Omnidirectional)** - can spin around the vertical axis
+ **Steered** - the spinning angle around the vertical axis is controllable
+ **Sweden** - can move vertical to the wheel plane

### Configuration on Robots



---
## Wheeled Robot Forward Kinematics 

+ **Goal** - Establish the global robot velocity vector $\dot{\xi}_I$ in terms of wheel spinning speeds

The kinematic analysis of wheels aims at building up the relationship between the global robot velocity and the wheels' spinning and steering speed

Since the robot system has a global fixed frame and a local body frame. A coordinate transform should be established to convert between global and local velocities.

The robot's global velocity on the horizontal plane is denoted as
$$\dot{\xi}_I=\begin{bmatrix}\dot{x}\\\dot{y}\\\dot{\theta}\end{bmatrix}$$
+ $\dot{x}$ - linear velocity along global $x$ axis
+ $\dot{y}$ - linear velocity along global $y$ axis
+ $\dot{\theta}$ - angular velocity (always the same on any frames)
+ $\theta$ - the directional angle between $X_I$ and $X_R$

### Coordinate Transform

The coordinate transform maps velocity from the local frame to the global frame. The $x$ axes angle $\theta$ is directional from $X_I$ to $X_R$ and can be negative.

+ From global $\dot{\xi}_{I}$ to local $\dot{\xi}_{R}$
$$\begin{cases}\dot{x}\cos\theta-\dot{y}\sin\theta=\dot{x}_r\\\dot{x}\sin\theta+\dot{y}\cos\theta=\dot{y}_r\end{cases}$$
$$\dot{\xi}_{R}=\begin{bmatrix}\cos\theta&\sin\theta&0\\-\sin\theta&\cos\theta&0\\0&0&1\end{bmatrix}\dot{\xi}_{I}=R(\theta)\dot{\xi}_I$$

+ From local $\dot{\xi}_{R}$ to global $\dot{\xi}_{I}$
$$\begin{cases}\dot{x}_r\cos\theta-\dot{y}_r\sin\theta=\dot{x}\\\dot{x}_r\sin\theta+\dot{y}_r\cos\theta=\dot{y}\end{cases}$$
$$\dot{\xi}_{I}=\begin{bmatrix}\cos\theta&-\sin\theta&0\\\sin\theta&\cos\theta&0\\0&0&1\end{bmatrix}\dot{\xi}_{R}=R^{-1}(\theta)\dot{\xi}_R$$
The two transform matrices are mutually inverses

### Wheel Constraint

There're basically two constraints on each wheel.

+ **Rolling** - The wheel must roll when the velocity is parallel to the wheel plane
+ **No Sliding** - The wheel should not move when the velocity is orthogonal to the wheel plane

---
## Wheel Constraint Models

Wheel Constraint Models build the relationship between the spinning and steering speeds of a single wheel and the local velocities $\dot{x}_r,\dot{y}_r,\dot{\theta}$ 

The equations of wheel constraint can be simply derived using geometry analysis.

+ **Rolling Equation** - The sum of factor velocities of $\dot{x}_r,\dot{y}_r,\dot{\theta}$ parallel to the wheel plane should be equal to wheel speed $v=\dot{\varphi}r$
+ **Orthogonal Equation** - The sum of factor velocities of $\dot{x}_r,\dot{y}_r,\dot{\theta}$ orthogonal to the wheel plane should be 0

### Standard Wheel (Fixed or Steered)

$$\begin{cases}\dot{x}_r\sin(\alpha+\beta)-\dot{y}\cos(\alpha+\beta)-l\dot{\theta}\cos\beta=v\\\dot{x}_r\cos(\alpha+\beta)+\dot{y}\sin(\alpha+\beta)+l\dot{\theta}\sin\beta=0\end{cases}$$
+ $\beta$ is defined as the angle between 

If the wheel can steer, the $\beta$ angle becomes a variable. 


![[Pasted image 20241126120250.png]]


### Castor Wheel

The constraint equations of castor wheels are mainly the same as standard wheels. The only difference is that the orthogonal equation now includes a velocity $d\dot{\beta}$ that provides by the steering.

$$\begin{cases}\dot{x}_r\sin(\alpha+\beta)-\dot{y}\cos(\alpha+\beta)-l\dot{\theta}\cos\beta=v\\\dot{x}_r\cos(\alpha+\beta)+\dot{y}\sin(\alpha+\beta)+l\dot{\theta}\sin\beta+\color{red}d\dot{\beta}\color{black}=0\end{cases}$$

![[Pasted image 20241126120317.png]]

### Sweden Wheel





![[Pasted image 20241126120351.png]]

---
## Robot kinematic Constraints






---
## Examples

### Differential Standard Wheels Driven

![[Pasted image 20241126101833.png]]



### Example 1 - Velocity Transform


### Example 2 - Rolling and Sliding Constraints for Fixed Wheel



### Example 3 -