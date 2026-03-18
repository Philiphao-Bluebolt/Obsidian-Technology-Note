+ **Goal** - Obtain joint parameters from a given tool configuration
+ **Approach** - Numerical vs Analytic

---
## Tool-configuration Vector

+ **Function** - Using only 6 parameters $(w_1...w_6)$ to represent tool position and orientation instead of 9 + 3 (Rotation Matrix + Translation Vector)

The Arm matrix of a robot, which transforms points from the tool frame to the base frame, is in the following form. $R$ is the rotation matrix and $p$ is the translation vector.

$$T_{base}^{tool}=\begin{bmatrix}&&&\\&R&&p\\&&&\\0&0&0&1\end{bmatrix}=\begin{bmatrix}&&&\\r_x&r_y&r_z&p\\&&&\\0&0&0&1\end{bmatrix}$$

Remember that the 3rd column vector $r_z$ in the rotation matrix is the orientation of tool frame reaching axis $z$ w.r.t the base frame. 

Using only $r_z$ and roll angle $q_n$ about $r_z$ is enough for representing tool orientation.

The tool configuration vector is given by
$$w=\begin{bmatrix}p\\e(q_n/\pi)r_z \end{bmatrix}$$

---
## Analytic Method

+ Known - Tool Configurations (As Tool-configuration Vector)
+ Unknown - Joint Parameters 
 
When using the analytic method to obtain the joint parameters, we're solving a equation in which tool configuration parameters are known and the joint parameters are unknown
$$w=\begin{bmatrix}w_1\\w_2\\w_3\\w_4\\w_5\\w_6\end{bmatrix}=\begin{bmatrix}p_x(q)\\p_y(q)\\p_z(q)\\r_x(q)\\r_y(q)\\r_z(q)\end{bmatrix}$$
