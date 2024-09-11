This part of example is related to the kinematic analysis of robot, mainly focusing on the calculation of Coordinate Transform 

+ [[#Direct Kinematics]]
	+ [[#2-2 Fundamental Rotation of mobile frame]]
	+ [[#2-3 Inverse Rotation Matrix]]
	+ [[#2-4 Composite Rotation Matrix]]
	+ [[#2-5 Yaw, Pitch, Roll rotation of the tool]]
	+ [[#2-6 Homogeneous Translation and Rotation]]
		+ [[#Question 1 - Translation]]
		+ [[#Question 2 - Rotation]]
	+ [[#2-7 Composite Homogeneous Transform (w.r.t the fixed frame)]]
	+ [[#2-8 Composite Homogeneous Transform (w.r.t the mobile frame)]]
	+ [[#2-9 Inverse of Homogeneous Transform]]


---
## Direct Kinematics


#### 2-2  Fundamental Rotation of mobile frame

> Suppose that $M$ is rotated about $f_x$ of $F$ by an angle $\phi=\pi/3$. If the coordinates of a point $p$ in $M$ are $p^M= [2, 0 , 3]^T$, what are the coordinates of $p$ in $F$?


The fundamental rotation around the $f_x$ axis of fixed frame $F$ is represented by the matrix
$$R_x(\phi)=\begin{bmatrix}
1 & 0 & 0\\ 
0 & \cos\phi & -\sin\phi\\ 
0 & \sin\phi & \cos\phi\\ 
\end{bmatrix}$$
Then we get the rotation matrix of $M$
$$R_{M\to F}=\begin{bmatrix}
1 & 0 & 0\\ 
0 & \cos (\frac{\pi}{3}) & -\sin(\frac{\pi}{3})\\ 
0 & \sin(\frac{\pi}{3}) & \cos(\frac{\pi}{3})\\ 
\end{bmatrix} =\begin{bmatrix}
1 & 0 & 0\\ 
0 & \frac{1}{2} & -\frac{\sqrt{3}}{2}\\ 
0 & \frac{\sqrt{3}}{2} & \frac{1}{2}\\ 
\end{bmatrix}$$
The coordinate of point $p$ in frame $F$ can be obtained by the rotation matrix
$$p^F=R p^M = \begin{bmatrix}
1 & 0 & 0\\ 
0 & \frac{1}{2} & -\frac{\sqrt{3}}{2}\\ 
0 & \frac{\sqrt{3}}{2} & \frac{1}{2}\\ 
\end{bmatrix} \begin{bmatrix}
2 \\ 
0 \\ 
3 \\ 
\end{bmatrix}=\begin{bmatrix}
2 \\ 
-\frac{3\sqrt{3}}{2} \\ 
\frac{3}{2} \\ 
\end{bmatrix}$$

#### 2-3  Inverse Rotation Matrix

> In example 2-2, suppose a point $q$ in $F$ has coordinates $q^F=[3,4,0]^T$. What are the coordinates of $q$ w.r.t the mobile coordinate frame $M$?


The rotation matrix mapping from $F$ to $M$ is the inverse of the matrix $R_{M\to F}$, which equal to the transpose of $R_{M\to F}$
$$R_{F \to M}=R_{M \to F}^{-1}=\begin{bmatrix}
1 & 0 & 0\\ 
0 & \frac{1}{2} & -\frac{\sqrt{3}}{2}\\ 
0 & \frac{\sqrt{3}}{2} & \frac{1}{2}\\ 
\end{bmatrix}^T=\begin{bmatrix}
1 & 0 & 0\\ 
0 & \frac{1}{2} & \frac{\sqrt{3}}{2}\\ 
0 & -\frac{\sqrt{3}}{2} & \frac{1}{2}\\ 
\end{bmatrix}$$
Then the answer is obvious
$$p^M=R_{F\to M}p^F=\begin{bmatrix}
1 & 0 & 0\\ 
0 & \frac{1}{2} & \frac{\sqrt{3}}{2}\\ 
0 & -\frac{\sqrt{3}}{2} & \frac{1}{2}\\ 
\end{bmatrix}\begin{bmatrix}3 \\ 4 \\ 0 \\ \end{bmatrix}=\begin{bmatrix}3 \\ 2 \\ -2\sqrt{3} \\ \end{bmatrix}$$
#### 2-4  Composite Rotation Matrix

> If $M$ is rotated by an angle $\beta$ about the 2nd axis of $F$, followed by a rotation of angle $\theta$ about the 3rd axis of $M$, followed by a rotation of angle $\alpha$ about the 1st axis of $M$, what is the composite rotation matrix describing the complete process?


Remember that rotation matrix around the fixed frame should be multipled on the left side and that rotation matrix around the mobile frame should be multipled on the right side.
$$R_{M\to F}=R(\beta)R(\theta)R(\alpha)$$

#### 2-5  Yaw, Pitch, Roll rotation of the tool

> Suppose we rotate the tool about the fixed axes starting with a yaw of $\pi/2$, followed by a pitch of -$\pi/2$ and, finally, a roll of $\pi/2$. What is the resulting composite rotation matrix?


The Yaw, Pitch, Roll angle of the tool represent the rotation angle around the 1st, 2nd, 3rd axis of the fixed frame respectly. With this information, the question can be treated as getting a simple composite rotation matrix.
$$R=R(R)R(P)R(Y)=\begin{bmatrix}
1 & 0 & 0\\ 0 & \cos(\frac{\pi}{2}) & -\sin(\frac{\pi}{2})\\ 0 & \sin(\frac{\pi}{2}) & \cos(\frac{\pi}{2})\\ 
\end{bmatrix}\begin{bmatrix}
\cos(-\frac{\pi}{2}) & 0 & \sin(-\frac{\pi}{2})\\ 
0 & 1 & 0\\ 
-\sin(-\frac{\pi}{2}) & 0 & \cos(-\frac{\pi}{2})\\ 
\end{bmatrix}\begin{bmatrix}
\cos(\frac{\pi}{2}) & -\sin(\frac{\pi}{2}) & 0\\ 
\sin(\frac{\pi}{2}) & \cos(\frac{\pi}{2}) & 0\\ 
0 & 0 & 1\\ 
\end{bmatrix}$$
Remember, rotation matrices around the fixed axis are multiplied to the left.
$$R=\begin{bmatrix} 0 & 0&1\\0&-1&0\\1&0&0\end{bmatrix}$$

#### 2-6  Homogeneous Translation and Rotation

##### Question 1 - Translation

> Suppose $q^M=[0,0,10,1]^T$. The mobile $M$ is translated 5 units along $f_x$ and -3 units along $f_y$ axis. Obtain the coordinate of point $q$ w.r.t fixed frame $F$


The transform matrix should multiple to the left if the translation is along the fixed frame. Then the Homogeneous Translation Matrix is
$$T_{trans}=T_yT_x=\begin{bmatrix}1&0&0&0\\0&1&0&-3\\0&0&1&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}1&0&0&5\\0&1&0&0\\0&0&1&0\\0&0&0&1\end{bmatrix}=\begin{bmatrix}1&0&0&5\\0&1&0&-3\\0&0&1&0\\0&0&0&1\end{bmatrix}$$
The coordinate of $q$ w.r.t fixed frame $F$ is
$$q^F=T_{trans}q^M=\begin{bmatrix}1&0&0&5\\0&1&0&-3\\0&0&1&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}0\\0\\10\\1\end{bmatrix}=\begin{bmatrix}5\\-3\\10\\1\end{bmatrix}$$
##### Question 2 - Rotation

> Given $q^M=[0,0,10,1]^T$. Suppose initially $M$ coincident with $F$ and is rotated by $\pi/4$ radians about $f_x$ . Obtain the coordinate of point $q$ w.r.t fixed frame $F$


As the rotation of mobile frame is w.r.t the fixed frame, the transform matrix should multiple to the left.
$$T_{rot}=\begin{bmatrix}1&0&0&0\\0&\cos(\frac{\pi}{4})&-\sin(\frac{\pi}{4})&0\\0&\sin(\frac{\pi}{4})&\cos(\frac{\pi}{4})&0\\0&0&0&1\end{bmatrix}=\begin{bmatrix}1&0&0&0\\0&\frac{\sqrt{2}}{2}&-\frac{\sqrt{2}}{2}&0\\0&\frac{\sqrt{2}}{2}&\frac{\sqrt{2}}{2}&0\\0&0&0&1\end{bmatrix}$$
Then we get $q^F$
$$q^F=T_{rot}q^M=\begin{bmatrix}1&0&0&0\\0&0.707&-0.707&0\\0&0.707&0.707&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}0\\0\\10\\1\end{bmatrix}=\begin{bmatrix}0\\-7.07\\7.07\\1\end{bmatrix}$$

#### 2-7   Composite Homogeneous Transform (w.r.t the fixed frame)

> Let $F=\{f_x,f_y,f_z\}$ and $M=\{m_x,m_y,m_z\}$ be two initially coincident fixed and mobile orthonormal coordinate frames, respectively. Suppose we translate $M$ along $f_y$ by 3 units and then rotate $M$ about $f_z$ by $\pi$ radians. Find $m_x$ with respect to $F$ after the composite transformation.


First, you need to calculate the transform matrix mapping from $M$ to $F$. All the transforms in this question are w.r.t the fixed frame, so all the transform matrices multiple to the left side.
$$T_{M\to F}=T_{rot}T_{trans}=\begin{bmatrix}\cos(\pi) & -\sin(\pi)&0 &0\\\sin(\pi) &\cos(\pi) & 0 &0\\ 0 & 0 & 1 &0\\0&0&0&1\end{bmatrix}\begin{bmatrix}1&0&0&0\\0&1&0&3\\0&0&1&0\\0&0&0&1\end{bmatrix}=\begin{bmatrix}-1 & 0&0 &0\\0 &-1 & 0 &-3\\ 0 & 0 & 1 &0\\0&0&0&1\end{bmatrix}$$
Then compute the coordinate of $m_x$ in $F$
$$f_{m_x}=T_{M\to F}m_x=\begin{bmatrix}-1 & 0&0 &0\\0 &-1 & 0 &-3\\ 0 & 0 & 1 &0\\0&0&0&1\end{bmatrix}\begin{bmatrix}1\\0\\ 0\\1\end{bmatrix}=\begin{bmatrix}-1\\-3\\ 0\\1\end{bmatrix}$$


#### 2-8  Composite Homogeneous Transform (w.r.t the mobile frame)

> Similar to 2-7, but this time we translate $M$ along $m_y$ by 3 units and then rotate $M$ about $m_z$ by $\pi$ radians. Find $m_x$ with respect to $F$ after the composite transformation.


The computing method is similar to which in 2-7, but all the transform are w.r.t the mobile frame this time, so we should multiple them to the right side
$$T_{M\to F}=T_{trans}T_{rot}=\begin{bmatrix}1&0&0&0\\0&1&0&3\\0&0&1&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}\cos(\pi) & -\sin(\pi)&0 &0\\\sin(\pi) &\cos(\pi) & 0 &0\\ 0 & 0 & 1 &0\\0&0&0&1\end{bmatrix}=\begin{bmatrix}-1&0&0&0\\0&-1&0&3\\0&0&1&0\\0&0&0&1\end{bmatrix}$$
Then compute the coordinate of $m_x$ in $F$
$$f_{m_x}=T_{M\to F}m_x=\begin{bmatrix}-1&0&0&0\\0&-1&0&3\\0&0&1&0\\0&0&0&1\end{bmatrix}\begin{bmatrix}1\\0\\ 0\\1\end{bmatrix}=\begin{bmatrix}-1\\3\\ 0\\1\end{bmatrix}$$


#### 2-9  Inverse of Homogeneous Transform

> Suppose the following homogeneous coordinate transformation matrix maps $M$ into $F$. Find the homogeneous coordinate transformation which maps $F$ into $M$ and use it to find $f_y$ with respect to $M$. 
> $$T=\begin{bmatrix}0&-1&0&0\\1&0&0&2\\0&0&1&2\\0&0&0&1\end{bmatrix}$$

First we calculate the inverse transform using the given inverse formula
$$T_{F\to M}=T^{-1}=\begin{bmatrix}
R^T & -R^Tp \\ 
0_{1\times3} & 1\\ 
\end{bmatrix}=\begin{bmatrix}0&1&0&-2\\-1&0&0&0\\0&0&1&-2\\0&0&0&1\end{bmatrix}$$
Then compute the coordinate of $f_y$ in $M$
$$M_{f_y}=T_{F\to M}f_y=\begin{bmatrix}0&1&0&-2\\-1&0&0&0\\0&0&1&-2\\0&0&0&1\end{bmatrix}\begin{bmatrix}0\\1\\ 0\\1\end{bmatrix}=\begin{bmatrix}-1\\0\\ -2\\1\end{bmatrix}$$

#### 2-10  Using DH Analysis on a Five-axis robot 

> Establishing joint axes and finding parameters of the given Microbot Alpha II model
![[Pasted image 20240828155704.png]]


> [!FAQ] Can I adjust the joints and make the gripper pointing to the sky so that the initial configuration will be simplier for analysis? 
> Yes, you can choose arbitrary initial configuration for analysis. 




---
## Inverse