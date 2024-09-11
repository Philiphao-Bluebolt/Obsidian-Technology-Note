+ **Goal** - Represent end-effector pose using joint parameters (Rotation Angles or Translation Distance)
+ **Mathematics** - Coordinate Transform
+ **Analysis** - DH Parameters

+ [[#Coordination of point]]
+ [[#Rotation Transform]]
	+ [[#Inverse Rotation]]
	+ [[#Fundamental Rotation]]
	+ [[#Composite Rotation]]
+ [[#Homogeneous Transform]]
	+ [[#Inverse Homogeneous Transform]]
	+ [[#Composite Homogeneous Transform]]
+ [[#DH Parameters Representation]]
	+ [[#Assign Frames]]
		+ [[#Origin Location]]
		+ [[#Axes Direction]]
	+ [[#Find DH Parameters]]
	+ [[#Write the Transform Matrices]]

---
## Coordination of point

Now assume we have two frame here in the 3D space, a fixed frame $F$ and a mobile frame $M$. They share the same origin. Here're their basis
$$\begin{align}F&=\{f_x,f_y,f_z\}\\
M&={\{m_x,m_y,m_z\}}
\end{align}$$
The coordination of a point $p$ in $R^3$ can be represented in linear combinations using the basis of the two frames respectively.
$$\begin{align}
p^F&=p_x^f f_x+p_y^f f_y+p_z^f f_z\\
p^M&=p_x^m m_x+m_y^f m_y+p_z^m m_z
\end{align}$$

---
## Rotation Transform

To describe the rotational motion of the robot, we need to use the **Rotation Transform Matrix**. This matrix maps a coordinate of a point from the mobile frame to the fixed frame.
$$
p^F=Rp^M
$$

The rotation matrix can be calculated as 

$$R=\begin{bmatrix}
f_x \cdot m_x & f_x \cdot m_y & f_x \cdot m_z \\ 
f_y \cdot m_x & f_y \cdot m_y & f_y \cdot m_z \\ 
f_z \cdot m_x & f_z \cdot m_x & f_z \cdot m_z \\ 
\end{bmatrix}$$

Here's a more comprehensible explanation:

> [!NOTE] Rotational Matrix
> The 3 columns of the rotation matrix mapping from $M$ to $F$ is actual basis vectors of the mobile frame $M$ represented in respect to the frame $F$

### Inverse Rotation

Every rotation matrix is a orthogonal matrix, which means
$$R^{-1}=R^T$$
The inverse mapping can be easily done by inverse matrix $R^{-1}$, it maps the coordinate of $p$ from the fixed frame to the mobile frame
$$p^M=R^{-1}p^F=R^Tp^F$$

### Fundamental Rotation

A fundamental rotation implies that frame $M$ only rotates around the axis of frame $F$ for once.

+ Rotate around $f_x$
$$R_x(\theta)=\begin{bmatrix}
1 & 0 & 0\\ 
0 & \cos\theta & -\sin\theta\\ 
0 & \sin\theta & \cos\theta\\ 
\end{bmatrix}$$
+ Rotate around $f_y$
$$R_y(\theta)=\begin{bmatrix}
\cos\theta & 0 & \sin\theta\\ 
0 & 1 & 0\\ 
-\sin\theta & 0 & \cos\theta\\ 
\end{bmatrix}$$
+ Rotate around $f_z$
$$R_z(\theta)=\begin{bmatrix}
\cos\theta & -\sin\theta & 0\\ 
\sin\theta & \cos\theta & 0\\ 
0 & 0 & 1\\ 
\end{bmatrix}$$
### Composite Rotation

Fundamental Rotation Matrices can be multipled together to form a sequence of rotation, which is called Composite Rotation

+ Multiple at the **front** - Rotate around an axis of the fixed frame $F$
+ Multiple at the **end** - Rotate around an axis of the mobile frame $M$

___
## Homogeneous Transform

The representation of translation is simple, it just need a translation vector $p$. The following equation maps the coordination of a point $q$ from the mobile frame $M$ to the fixed frame $F$
$$q^F=q^M + p$$
The definition of Homogeneous Transformation Matrix is aimed at unifying the translation and orientation motion into the same matrix and directly using matrix multiplication to calculate the transform.
$$T=\begin{bmatrix}
R_{3\times3} & p_{3\times1} \\ 
0_{1\times3} & 1\\
\end{bmatrix}$$
+ Homogeneous-form points
$$q=\begin{bmatrix}
q_x & q_y & q_z & 1 \\ 
\end{bmatrix}^T$$
+ Homogeneous Translation (Translation Vector $q$)
$$Tran(q)=\begin{bmatrix}
1 & 0 & 0 & p_1\\ 
0 & 1 & 0 & p_2\\
0 & 0 & 1 & p_3\\ 
0 & 0 & 0 & 1\\ 
\end{bmatrix}$$
+ Homogeneous Rotation (Rotation Matrix $R$)
$$Rot(R)=\begin{bmatrix}
 &  & & 0\\ 
 & R & & 0\\
 &  &  & 0\\ 
0 & 0 & 0 & 1\\ 
\end{bmatrix}$$

### Inverse Homogeneous Transform

The inverse of  $T$ is 
$$T^{-1}=\begin{bmatrix}
R^T & -R^Tp \\ 
0_{1\times3} & 1\\ 
\end{bmatrix}$$

### Composite Homogeneous Transform

Just like rotation matrix, the homogeneous matrices can be multipled into composite ones, which represents more complicated transform. 

+ Multiple at the **front** - Rotate around or Translate along an axis of the fixed frame $F$
+ Multiple at the **end** - Rotate around or Translate along an axis of the mobile frame $M$


---
## DH Parameters Representation

+ **Function** - Transform points from mobile **tool frame** to the fixed **base frame**
+ **Final Result** - An arm equation
+ **Stages**:
	1. Identify every joint and link as well as base and end-effector of the robot
	2. Assign **link** frames
	3. Find the four DH Parameters between two adjacent frames
	4. Write down the transform matrices $T$ between every two frames
	5. Get the transform matrix  $T_{base}^{tool}$  mapping from tool frame to the base frame 

### Assign Frames

A $n$ axes robot consists of 

+ $n$ joints
+ $n$ links (including Base as Link 0)
+ one tool (end-effector)

A number of $n+1$ frames would be assigned

+ $n$ link frames 
+ one tool frame

#### Origin Location

 Every established Frame $k$ will be originated at the intersection of Link $k$ and Joint $k+1$. Notice that Frame 0 located at the intersection of Base and Joint 1.
 

![[Pasted image 20240911151348.png]]

The last frame is **Tool Frame**, whose origin is at the tool tip.

#### Axes Direction

For the link frames

+ Axis $z$ of Frame $k$ should align with the axis of Joint $k+1$
+ Axis $x$ of Frame $k$ is better parallel with axis $x$ of Frame $k-1$ 

For tool frame

+ Axis $z$ point to the direction of reaching forward
+ Axis $y$ point to the sliding direction

### Find DH Parameters

There are $n$ sets of parameters for $n+1$ frames, each set has four parameters, two joint parameters and two link parameters.

+ For revolute joint $k-1$, the Joint Angle $\theta_k$ is a variable
+ For prismatic joint $k-1$, the Joint Distance $d_k$ is a variable

| Parameter        |   Symbol   | Definition                                           |
| ---------------- | :--------: | ---------------------------------------------------- |
| Joint Angle      | $\theta_k$ | Angle between $x_{k-1}$ and $x_k$ about $z_{k-1}$    |
| Joint Distance   |   $d_k$    | Distance between $x_{k-1}$ and $x_k$ along $z_{k-1}$ |
| Link Length      |   $a_k$    | Distance between $z_{k-1}$ and $z_k$ along $x_k$     |
| Link Twist Angle | $\alpha_k$ | Angle between $z_{k-1}$ and $z_k$ about $x_k$        |

### Write the Transform Matrices

The homogeneous transform matrix mapping from Frame $k$ to Frame $k-1$ can be represented by DH parameters as
$$T^{k}_{k-1}=\begin{bmatrix} \cos\theta_k & -\cos\alpha_k\sin\theta_k& \sin\alpha_k\sin\theta_k & a_k \cos\theta_k \\ \sin\theta_k & \cos\alpha_k\cos\theta_k& -\sin\alpha_k\cos\theta_k & a_k \sin\theta_k \\ 0 & \sin\alpha_k & \cos\alpha_k & d_k\\ 0 &0&0&1\end{bmatrix}$$
$$p_{k-1}=T^k_{k-1}p_k$$
Unify the symbol of joint variables as $q$, it represents $\theta_k$ for revolute joint and $d_k$ for prismatic joint

The transform matrix  $T_{base}^{tool}$  from tool to base
$$T_{base}^{tool}=T_0^1(q_1)T_1^2(q_2)...T_{n-1}^{n}(q_{n})$$

### The Arm Equation

The arm equation is 