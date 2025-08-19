[[#Queation 1]]
[[#Queation 2]]

![[Assignment for Kinematics.pdf]]

![[EE6221_Assignment_solution(1).pdf]]

---
## Queation 1

### (a)  Assign frames and DH parameters

First we assign the frames.

![[Pasted image 20240925123355.png]]

Then find the parameters for every axes ($l=200mm$)

| Axis | $\theta_k$ | $d_k$ | $a_k$ | $\alpha_k$ |
| ---- | :--------: | :---: | :---: | :--------: |
| 1    |  $-\pi/2$  | $d_1$ |   0   |  $-\pi/2$  |
| 2    |  $-\pi/2$  | $d_2$ |   0   |  $\pi/2$   |
| 3    | $\theta_3$ |   0   |   0   |  $-\pi/2$  |
| 4    | $\theta_4$ |  $l$  |   0   |     0      |

### (b)  Obtain Arm Matrix

Write down the matrices between each two adjacent frames.
$$T^{k}_{k-1}=\begin{bmatrix} \cos\theta_k & -\cos\alpha_k\sin\theta_k& \sin\alpha_k\sin\theta_k & a_k \cos\theta_k \\ \sin\theta_k & \cos\alpha_k\cos\theta_k& -\sin\alpha_k\cos\theta_k & a_k \sin\theta_k \\ 0 & \sin\alpha_k & \cos\alpha_k & d_k\\ 0 &0&0&1\end{bmatrix}$$
$$T_0^1=\begin{bmatrix} 0&0&1&0\\-1&0&0&0\\0&-1&0&d_1\\0&0&0&1\end{bmatrix}$$
$$T_1^2=\begin{bmatrix}0&0&-1&0\\-1&0&0&0\\0&1&0&d_2\\0&0&0&1\\\end{bmatrix}$$
$$T_2^3=\begin{bmatrix}\cos\theta_3&0&-\sin\theta_3&0\\\sin\theta_3&0&\cos\theta_3&0\\0&-1&0&0\\0&0&0&1\\\end{bmatrix}$$
$$T_3^4=\begin{bmatrix}\cos\theta_4&-\sin\theta_4&0&0\\\sin\theta_4&\cos\theta_4&0&0\\0&0&1&l\\0&0&0&1\\\end{bmatrix}$$
Then, we must identify the major axes from the joints. Usually, the first three axes are major axes but the situation changes in this robot. The robot here only has 2 degrees of freedom on translation, so only the first two axes are major axes.
$$T_{base}^{wrist}=T_0^1T_1^2=\begin{bmatrix} 0&0&1&0\\-1&0&0&0\\0&-1&0&d_1\\0&0&0&1\\\end{bmatrix}\begin{bmatrix}0&0&-1&0\\-1&0&0&0\\0&1&0&d_2\\0&0&0&1\\\end{bmatrix}=\begin{bmatrix}0&1&0&d_2\\0&0&1&0\\1&0&0&d_1\\0&0&0&1\\\end{bmatrix}$$
$$T_{wrist}^{tool}=T_2^3T_3^4=\begin{bmatrix}C_3&0&-S_3&0\\S_3&0&C_3&0\\0&-1&0&0\\0&0&0&1\\\end{bmatrix}\begin{bmatrix}C_4&-S_4&0&0\\S_4&C_4&0&0\\0&0&1&l\\0&0&0&1\\\end{bmatrix}=\begin{bmatrix}C_3C_4&-C_3S_4&-S_3&-0.2S_3\\S_3C_4&-S_3S_4&C_3&0.2C_3\\-S_4&-C_4&0&0\\0&0&0&1\\\end{bmatrix}$$
The complete arm matrix
$$T_{base}^{tool}=T_{base}^{wrist}T_{wrist}^{tool}=\begin{bmatrix}0&1&0&d_2\\0&0&1&0\\1&0&0&d_1\\0&0&0&1\\\end{bmatrix}\begin{bmatrix}C_3C_4&-C_3S_4&-S_3&-0.2S_3\\S_3C_4&-S_3S_4&C_3&0.2C_3\\-S_4&-C_4&0&0\\0&0&0&1\\\end{bmatrix}=\begin{bmatrix}S_3C_4&-S_3S_4&C_3&0.2C_3+d_2\\-S_4&-C_4&0&0\\C_3C_4&-C_3S_4&-S_3&-0.2S_3+d_1\\0&0&0&1\end{bmatrix}$$

### (c)  Obtain tool configuration vector and solve inverse kinematics

We'll use the analytic approach for calculation.

The reaching axis of the tool frame w.r.t the base frame is 
$$r_z=\begin{bmatrix}C_3\\0\\-S_3\end{bmatrix}$$
Since joint 4 controls the roll angle of the tool, the tool configuration vector is
$$w=\begin{bmatrix}p\\\exp(q_n/\pi)r_z\end{bmatrix}=\begin{bmatrix}0.2C_3+d_2\\0\\-0.2S_3+d_1\\e^{q_4/\pi}C_3\\0\\-e^{q_4/\pi}S_3\end{bmatrix}=\begin{bmatrix}w_1\\w_2\\w_3\\w_4\\w_5\\w_6\end{bmatrix}$$
Firstly, we obtain $q_4$ by temporarily eliminating $q_3$ using the square sum of $w_4$ and $w_6$
$$\begin{align}w^2_4+w^2_6&=(e^{q_4/\pi}C_3)^2+(-e^{q_4/\pi}S_3)^2=e^{2q_4/\pi}\\q_4&=\frac{\pi\ln(w^2_4+w_6^2)}{2}\end{align}$$
Then, $q_3$ can be solved by using the atan2 function
$$\begin{align}\frac{w_6}{w_4}&=-\frac{e^{q_4/\pi}S_3}{e^{q_4/\pi}C_3}=-\tan q_3\\q_3&=\arctan_2(-\frac{w_6}{w_4})\end{align}$$
Then $d_1$ and $d_2$ is within reach
$$\begin{align}d_1&=w_3+0.2S_3\\d_2&=w_1-0.2C_3\end{align}$$
All the joint variables solved from inverse analysis
$$\begin{cases}d_1=q_1=w_3+0.2S_3\\d_2=q_2=w_1-0.2C_3\\\theta_3=q_3=\arctan_2(-\frac{w_6}{w_4})\\\theta_4=q_4={\pi\ln(w^2_4+w_6^2)}/{2}\end{cases}$$

### (d)  Obtain the Jacobian Matrix for tool configuration

The tool configuration vector has been obtained in the last question
$$w=\begin{bmatrix}0.2C_3+d_2\\0\\-0.2S_3+d_1\\e^{q_4/\pi}C_3\\0\\-e^{q_4/\pi}S_3\end{bmatrix}$$
Since the Jacobian Matrix maps the joint space velocity to the tool-configuration velocity, it has a size of 6x4 here. Each of the column is the partial differential of a joint parameter with the same index.
$$\begin{align}V(q)&=\begin{bmatrix}\frac{\partial w}{\partial q_1}& \frac{\partial w}{\partial q_2} &\frac{\partial w}{\partial q_3}& \frac{\partial w}{\partial q_4}  \end{bmatrix} \\&=\begin{bmatrix}0&1&-0.2S_3&0\\0&0&0&0\\1&0&-0.2C_3&0\\0&0&-e^{q_4/\pi}S_3&\frac{e^{q_4/\pi}}{\pi}C_3\\0&0&0&0\\0&0&-e^{q_4/\pi}C_3&-\frac{e^{q_4/\pi}}{\pi}S_3\end{bmatrix}\end{align}$$



---
## Queation 2

### (a)  Arm Matrix for picking up part A

The workstation described in the queation uses only the base frame, so we don't need to do complex transform in the answer.

When picking up part A, the grabber's reaching axis $r_z$ points down and its sliding axis $r_y$ points right (or left). Which means that
$$r_z=-z_0$$
$$r_y=x_0 \quad or\quad -x_0$$
As we know that the three column vectors of the rotation matrix represents the coordinates of three mobile axis vectors w.r.t the fixed frame. We can write down the rotation matrix of the grabber w.r.t the base frame.
$$R=\begin{bmatrix}0&1&0\\1&0&0\\0&0&-1\\\end{bmatrix}\quad or\quad\begin{bmatrix}0&-1&0\\-1&0&0\\0&0&-1\\\end{bmatrix}$$
The translation vector of the grabber equal to the coordinate of part A
$$p=\begin{bmatrix}6\\12\\2\\\end{bmatrix}$$
Then we combine them to get the transform matrix
$$T_{base}^{part}=\begin{bmatrix}0&1&0&6\\1&0&0&12\\0&0&-1&2\\0&0&0&1\end{bmatrix}\quad or\quad\begin{bmatrix}0&-1&0&6\\-1&0&0&12\\0&0&-1&2\\0&0&0&1\end{bmatrix}$$

### (b)  Arm Matrix for placing part A on top of B

To put A on top of B, the targeted translation should be the coordinate of B replacing the height with the height sum of part A and B. To align their major axes, the grabber's sliding vector should rotate 90 degree w.r.t which when picking up A
$$T_{base}^{part}=\begin{bmatrix}-1&0&0&10\\0&1&0&5\\0&0&-1&4\\0&0&0&1\end{bmatrix} \quad or \quad\begin{bmatrix}1&0&0&10\\0&-1&0&5\\0&0&-1&4\\0&0&0&1\end{bmatrix}$$
