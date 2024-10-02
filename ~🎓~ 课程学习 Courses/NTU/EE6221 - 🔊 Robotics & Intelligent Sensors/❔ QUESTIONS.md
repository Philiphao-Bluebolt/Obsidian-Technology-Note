
---
## Kinematics

### Coordinate Transformation


> [!FAQ] Why is rotation matrix around the mobile frame multiplied to the right side, is there any intrinsic mathematical explanation?

### DH Parameters

> [!FAQ] What is the word "axis" in "five-axis robot" means? Does it simply refer to the joint? 
> It actually means degree of freedom

> [!FAQ] In DH Parameters, why are the transform matrices near the tool multiplied to the right?
> Because when using the arm matrix to transform point from tool frame (Frame $n$) to fixed base frame (Frame 0) $q_{base}=T^{tool}_{base}q_{tool}=T_0^1T_1^2T_2^3...T_{n-1}^{n}q_{tool}$, the process is done step by step. It means that the point is first transformed to the Frame $n-1$ then to the Frame $n-2$, and at last to the base frame.
> $$\begin{align}q_{base}=T^{tool}_{base}q_{tool}&=T_0^1T_1^2T_2^3...T_{n-1}^{n}q_{tool}\\&=T_0^1T_1^2T_2^3...q_{n-1}\\&=q_0\end{align}$$

> [!FAQ] In DH Parameters, when assigning DH parameters to axis, is it possible that both the link length $a_k$ and joint distance $d_k$ is 0 for two non-coincident frames? If it happens, does it means the assignment of frames is incorrect?
> Contents

> [!FAQ] If there is a initial angle $\theta_0$ between the $x_k$ and $x_{k-1}$ about $z_{k-1}$ for a rotation joint. Which one should the joint angle be, $\theta_k$ or $\theta_k + \theta_0$
> It should be $\theta_k$
