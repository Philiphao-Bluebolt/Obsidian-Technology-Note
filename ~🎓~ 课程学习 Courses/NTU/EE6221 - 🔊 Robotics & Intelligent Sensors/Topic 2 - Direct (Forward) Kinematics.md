Direct Kinematics focuses on the representation of end-effector pose using joint parameters (Rotation Angles or Translation Distance)

+ [[#Coordination of point]]
+ [[#Rotation Transform]]
	+ [[#Inverse Rotation]]
	+ [[#Fundamental Rotation]]
	+ [[#Composite Rotation]]
+ [[#Homogeneous Transform]]
	+ [[#Inverse Homogeneous Transform]]
	+ [[#Composite Homogeneous Transform]]
+ [[#DH Parameters]]

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
$$p^M=R^{-1}p^F=R^Tp^f$$

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

The representation of translation is simple, it just need a translation vector $p$
$$p^F=p^M + p$$
The definition of Homogeneous Transformation Matrix is aimed at unifying the translation and orientation motion in the same matrix and using matrix multiplication to calculate the transform.
$$T=\begin{bmatrix}
R_{3\times3} & p_{3\times1} \\ 
0_{1\times3} & 1\\
\end{bmatrix}$$
+ Homogeneous-form points
$$p=\begin{bmatrix}
p_x & p_y & p_z & 1 \\ 
\end{bmatrix}^T$$
+ Homogeneous Translation (Translation Vector $q$)
$$Tran(q)=\begin{bmatrix}
1 & 0 & 0 & q_1\\ 
0 & 1 & 0 & q_2\\
0 & 0 & 1 & q_3\\ 
0 & 0 & 0 & 1\\ 
\end{bmatrix}$$
+ Homogeneous Rotation (Rotation Matrix $R$)
$$Tran(q)=\begin{bmatrix}
 &  & & 0\\ 
 & R_{3\times3} & & 0\\
 &  &  & 0\\ 
0 & 0 & 0 & 1\\ 
\end{bmatrix}$$

### Inverse Homogeneous Transform

The inverse of Homogeneous Transform $T$ is 
$$T^{-1}=\begin{bmatrix}
R^T & -R^Tp \\ 
0_{1\times3} & 1\\ 
\end{bmatrix}$$

### Composite Homogeneous Transform




---
## DH Parameters

