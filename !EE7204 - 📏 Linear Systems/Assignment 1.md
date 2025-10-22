
+ [Question 1](#Question%201)
+ [Question 2](#Question%202)
+ [Question 3](#Question%203)
+ [Question 4](#Question%204)
+ [Question 5](#Question%205)

---
## Question 1

### (a) Differential Equations

Expand the differentials in the equations of two forces $F_x, F_y$ that act on the proof mass
$$\begin{cases}F_x=m\frac{\mathrm{d}^2}{\mathrm{d}t^2}(x_c+L\sin\theta)=m\ddot{x}_c+mL\ddot{\theta}\cos\theta-mL\dot{\theta}^2\sin\theta\\F_y=m\frac{\mathrm{d}^2}{\mathrm{d}t^2}(L\cos\theta)=-mL(\ddot{\theta}\sin\theta+\dot{\theta}^2\cos\theta)\end{cases}$$
Replace the variables $F_x, F_y$ in the torque equation of the proof mass and the Newton's law equation of the platform
$$\begin{align}I\ddot{\theta}&=u+F_yL\sin\theta-F_xL\cos\theta\\&=u-mL(\dot\theta^2\cos\theta+\ddot{\theta}\sin\theta)L\sin\theta-mL\ddot{x}_c\cos\theta-mL^2\ddot{\theta}\cos^2\theta+mL^2\dot{\theta}^2\sin\theta\cos\theta\\&=u-mL\ddot{x}_c\cos\theta-mL^2\ddot{\theta}\end{align}$$
$$\begin{align}M\ddot{x}_c&=-F_x-kx_c\\&=-m\ddot{x}_c-mL\ddot{\theta}\cos\theta+mL\dot{\theta}^2\sin\theta-kx_c\end{align}$$
The differential equations are derived
$$\begin{cases}(I+mL^2)\ddot{\theta}+mL\ddot{x}_c\cos\theta=u\\mL\cos(\theta)\ddot{\theta}+(M+m)\ddot{x}_c=mL\dot{\theta}^2\sin\theta-kx_c\end{cases}$$
$$\begin{bmatrix}I+mL^2&mL\cos\theta\\mL\cos\theta&M+m\end{bmatrix}\begin{bmatrix}\ddot{\theta}\\\ddot{x}_c\end{bmatrix}=\begin{bmatrix}u\\mL\dot{\theta}^2\sin\theta-kx_c\end{bmatrix}$$
Move the second-order coefficient matrix to the right side through matrix inversion
$$\begin{bmatrix}\ddot{\theta}\\\ddot{x}_c\end{bmatrix}=\frac{1}{\Delta(\theta)}\begin{bmatrix}M+m&-mL\cos\theta\\-mL\cos\theta&I+mL^2\end{bmatrix}\begin{bmatrix}u\\mL\dot{\theta}^2\sin\theta-kx_c\end{bmatrix}$$
$$\Delta(\theta)=(I+mL^2)(M+m)-m^2L^2\cos^2\theta$$


### (b) State Space Representation

Since the state variables were predefined as $x_1=\theta, x_2=\dot{\theta},x_3=x_c,x_4=\dot{x}_c$, the state space can be derived from the following equations
$$\begin{cases}\dot{x}_1=x_2\\\dot{x}_3=x_4\end{cases}$$
$$\begin{bmatrix}\ddot{\theta}\\\ddot{x}_c\end{bmatrix}=\frac{1}{\Delta(\theta)}\begin{bmatrix}M+m&-mL\cos\theta\\-mL\cos\theta&I+mL^2\end{bmatrix}\begin{bmatrix}u\\mL\dot{\theta}^2\sin\theta-kx_c\end{bmatrix}$$

The state transition equation of the mechanical system:
$$\begin{bmatrix}\dot{x}_1\\\dot{x}_2\\\dot{x}_3\\\dot{x}_4\end{bmatrix}=\begin{bmatrix}0&1&0&0\\0 &\frac{-m^2L^2\dot{\theta}\sin\theta\cos\theta}{\Delta(\theta)}&\frac{mLk\cos\theta}{\Delta(\theta)}&0\\0&0&0&1\\0&\frac{(I+mL^2)mL\dot{\theta}\sin\theta}{\Delta(\theta)}&\frac{-k(I+mL^2)}{\Delta(\theta)}&0\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}+\begin{bmatrix}0\\\frac{M+m}{\Delta(\theta)}\\0\\\frac{-mL\cos\theta}{\Delta(\theta)}\end{bmatrix}u$$

### (c) Equilibrium Points and Linearization

The nonlinear system reaches equilibrium when $\dot{x}=f(x)=0$, meaning that 
$$\begin{bmatrix}0&1&0&0\\0 &\frac{-m^2L^2\dot{\theta}\sin\theta\cos\theta}{\Delta(\theta)}&\frac{mLk\cos\theta}{\Delta(\theta)}&0\\0&0&0&1\\0&\frac{(I+mL^2)mL\dot{\theta}\sin\theta}{\Delta(\theta)}&\frac{-k(I+mL^2)}{\Delta(\theta)}&0\end{bmatrix}\begin{bmatrix}x_1\\x_2\\x_3\\x_4\end{bmatrix}+\begin{bmatrix}0\\\frac{M+m}{\Delta(\theta)}\\0\\\frac{-mL\cos\theta}{\Delta(\theta)}\end{bmatrix}u=0$$
First, it's obvious that $x_2$ and $x_4$ should be zero.
$$\begin{cases}x_2=0\\x_4=0\end{cases}$$
Since $x_2=\dot{\theta}$, all the coefficients containing $\dot{\theta}$ becomes zero. The two remain equations contain $x_3$ and $u$. 
$$\begin{cases}(mLk\cos\theta) x_3+(M+m)u=0\\-k(I+mL^2)x_3-(mL\cos\theta )u=0\end{cases}$$
+ If $x_3=0$ and $u=0$, there're equilibrium points no matter what the value of $x_1$ is.
+ If one of $x_3$ and $u$ is zero, there're no equilibrium points since the coefficients are non-zero
+ If $x_3\neq0$ and $u\neq0$, there exists no solution because the transition matrix is always invertible
$$\Delta(\theta)=(I+mL^2)(M+m)-m^2L^2\cos^2\theta\neq0$$
Therefore, the equilibrium points exist when states $x_2$, $x_3$ and $x_4$ and input $u$ are zero, with arbitrary value of $x_1$ 
$$(x_1,0,0,0)\quad x_1=\theta\in R$$

Linearize the system at point $(0,0,0,0)$, let $\dot{x}=f(x)$
$$\dot{x}\approx f(0)+\frac{\mathrm{d}\dot{x}}{\mathrm{d}x}|_{x=0}\ x=\begin{bmatrix}0&1&0&0\\0&0&\frac{mLk}{\Delta(0)}&0\\0&0&0&1\\0&0&\frac{-k(I+mL^2)}{\Delta(0)}&0\end{bmatrix}x$$
The linearized system 
$$\dot{x}=\begin{bmatrix}0&1&0&0\\0&0&\frac{mLk}{\Delta(0)}&0\\0&0&0&1\\0&0&\frac{-k(I+mL^2)}{\Delta(0)}&0\end{bmatrix}x+\begin{bmatrix}0\\\frac{M+m}{\Delta(0)}\\0\\\frac{-mL\cos\theta}{\Delta(0)}\end{bmatrix}u$$
$$\Delta(0)=(I+mL^2)(M+m)-m^2L^2$$


---
## Question 2

### (a)

> **Matrix $A_1$**

Calculate the eigenvalue and eigenvectors of $A_1$
$$\begin{align}A_1-\lambda I=\begin{bmatrix}1-\lambda&0&2\\0&1-\lambda&0\\0&0&-(1+\lambda)\end{bmatrix}&=0\\-(1-\lambda)^2(1+\lambda)&=0\\\end{align}$$
$$\begin{cases}\lambda_1=-1\\\lambda_2=\lambda_3=1\end{cases}$$
$$\begin{align}(A_1-\lambda_1I)v_1=\begin{bmatrix}2&0&2\\0&2&0\\0&0&0\end{bmatrix}v_1&=0\\v_1&=\begin{bmatrix}a\\0\\-a\end{bmatrix}\quad (a\in R,a\neq0)\end{align}$$
$$\begin{align}(A_1-\lambda_2I)v_2=\begin{bmatrix}0&0&2\\0&0&0\\0&0&-2\end{bmatrix}v_2&=0\\v_2&=\begin{bmatrix}a\\b\\0\end{bmatrix}\quad (a,b\in R,a\neq0,b\neq0)\end{align}$$
$$\begin{align}(A_1-\lambda_3I)v_3=\begin{bmatrix}0&0&2\\0&0&0\\0&0&-2\end{bmatrix}v_3&=v_2\\v_3&=\begin{bmatrix}a\\b\\0\end{bmatrix}\quad (a,b\in R,a\neq0,b\neq0)\end{align}$$
Diagonalization
$$P^{-1}A_1P=\begin{bmatrix} 0& 0&-1\\1&0 &1\\0&1&0\end{bmatrix}\begin{bmatrix}1&0&2\\0&1&0\\0&0&-1\end{bmatrix}\begin{bmatrix}1 &1 &0\\0 & 0&1\\-1&0&0\end{bmatrix}=\begin{bmatrix}-1 &0 &0\\0 & 1&0\\0&0&1\end{bmatrix}$$
Calculate $e^{A_1t}$
$$\begin{align}e^{A_1t}&=\mathcal{L}^{-1}\{(sI-A_1)^{-1}\}\\&=\mathcal{L}^{-1}\{\begin{bmatrix}s+1&0&-2\\0&s-1&0\\0&0&s-1\end{bmatrix}^{-1}\}\\&=\mathcal{L}^{-1}\{\begin{bmatrix}\frac{1}{s+1}&0&\frac{2}{(s+1)(s-1)}\\0&\frac{1}{s-1}&0\\0&0&\frac{1}{s-1}\end{bmatrix}\}\\&=\begin{bmatrix}e^{-t}&0&e^{t}-e^{-t}\\0&e^{t}&0\\0&0&e^t\end{bmatrix}\end{align}$$
> **Matrix $A_2$

Calculate the eigenvalue and eigenvectors of $A_2$
$$\begin{align}A_2-\lambda I=\begin{bmatrix}1-\lambda&0&-1\\0&1-\lambda&0\\1&0&-(1+\lambda)\end{bmatrix}&=0\\(1-\lambda)-(1-\lambda)^2(1+\lambda)&=0\end{align}$$
$$\begin{cases}\lambda_1=1\\\lambda_2=\lambda_3=0\end{cases}$$
$$\begin{align}(A_2-\lambda_1I)v_1=\begin{bmatrix}0&0&-1\\0&0&0\\1&0&-2\end{bmatrix}v_1&=0\\v_1&=\begin{bmatrix}0\\a\\0\end{bmatrix}\quad a\in R\end{align}$$
$$\begin{align}(A_2-\lambda_2 I)v_2=\begin{bmatrix}1&0&-1\\0&1&0\\1&0&-1\end{bmatrix}v_2&=0\\v_2&=\begin{bmatrix}a\\0\\a\end{bmatrix}\quad a\in R\end{align}$$
$$\begin{align}(A_2-\lambda_3I)v_3=\begin{bmatrix}1&0&-1\\0&1&0\\1&0&-1\end{bmatrix}v_3&=v_2\\v_3&=\begin{bmatrix}a+1\\0\\a\end{bmatrix}\quad a\in R\end{align}$$
Diagonalization
$$P^{-1}AP=\begin{bmatrix}0&1&0\\1&0&0\\0&0&1\end{bmatrix}\begin{bmatrix}1&0&-1\\0&1&0\\1&0&-1\end{bmatrix}\begin{bmatrix}0&1&0\\1&0&0\\0&0&1\end{bmatrix}=\begin{bmatrix}1&0&0\\0&0&1\\0&0&0\end{bmatrix}$$
Calculate $e^{A_2t}$
$$\begin{align}e^{A_2t}&=\mathcal{L}^{-1}\{(sI-A_2)^{-1}\}\\&=\mathcal{L}^{-1}\{\begin{bmatrix}s-1&0&1\\0&s-1&0\\-1&0&s-1\end{bmatrix}^{-1}\}\\&=\mathcal{L}^{-1}\{\begin{bmatrix}\frac{s-1}{s^2-2s+2}&0&-\frac{1}{s^2-2s+2}\\0&\frac{1}{s-1}&0\\\frac{1}{s^2-2s+2}&0&\frac{s-1}{s^2-2s+2}\end{bmatrix}\}\\&=\begin{bmatrix}e^t\cos t&0&-e^t\sin t\\0&e^t&0\\e^t\sin t&0&e^t\cos t\end{bmatrix}\end{align}$$
### (b)

The state transition matrix
$$\Phi(t)=e^{At}=\mathcal{L}^{-1}\{(sI-A)^{-1}\}=\mathcal{L}^{-1}\{\begin{bmatrix}s&-\omega\\\omega&s\end{bmatrix}^{-1}\}=\mathcal{L}^{-1}\{\begin{bmatrix}\frac{s}{s^2+\omega^2}&\frac{\omega}{s^2+\omega^2}\\-\frac{\omega}{s^2+\omega^2}&\frac{s}{s^2+\omega^2}\end{bmatrix}\}=\begin{bmatrix}\cos\omega t&\sin\omega t\\-\sin\omega t&\cos\omega t\end{bmatrix}$$
The solution of the continuous system is written as
$$\begin{align}x(t)&=\Phi(t) x(0)+\int_{0}^t \Phi(t-\tau)Bu(\tau)\mathrm{d}\tau \quad t\geq0\\&=\begin{bmatrix}\cos\omega t&\sin\omega t\\-\sin\omega t&\cos\omega t\end{bmatrix}\begin{bmatrix}1\\0\end{bmatrix}+\int_0^t\begin{bmatrix}\cos\omega (t-\tau)&\sin\omega (t-\tau)\\-\sin\omega (t-\tau)&\cos\omega (t-\tau)\end{bmatrix} \begin{bmatrix}0\\1\end{bmatrix}\mathrm{d}\tau\\&=\begin{bmatrix}\cos\omega t\\-\sin\omega t\end{bmatrix}+\begin{bmatrix}\frac{1}{\omega}\cos\omega(t-\tau)\\-\frac{1}{\omega}\sin\omega(t-\tau)\end{bmatrix}|_0^t\\&=\begin{bmatrix}\frac{1}{\omega}+\frac{\omega-1}{\omega}\cos\omega t\\\frac{1-\omega}{\omega}
\sin\omega t\end{bmatrix}\end{align}$$
The output of the system
$$y(t)=\begin{bmatrix}\frac{1}{\omega}+\frac{\omega-1}{\omega}\cos\omega t\\\frac{1-\omega}{\omega}
\sin\omega t\end{bmatrix}\begin{bmatrix}1&0\end{bmatrix}=\frac{1}{\omega}+\frac{\omega-1}{\omega}\cos\omega t$$

---
## Question 3

### (a)

The derivative of the chosen Lyaponuv function representing power of the system
$$\begin{align}\dot{V}(x)&=2\alpha x_1\dot{x}_1+2\beta x_2\dot{x}_2=-2\alpha^2x_1^2-2\beta^2x_2^2+2x_1x_2(\alpha\cos\omega t+\beta \sin\omega t)\\\end{align}$$
The power of the system shall decay for it to be asymptotically stable
$$\begin{align}-2\alpha^2x_1^2-2\beta^2x_2^2+2x_1x_2(\alpha\cos\omega t+\beta \sin\omega t)&\leq0\\x_1x_2(\alpha\cos\omega t+\beta \sin\omega t)&\leq\alpha^2x_1^2+\beta^2x_2^2\end{align}$$
The inequation can be expanded as
$$\alpha \cos\omega t+\beta \sin\omega t\leq\sqrt{\alpha^2+\beta^2}$$
$$2|x_1x_2|\leq\frac{\alpha}{\beta}x_1^2+\frac{\beta}{\alpha}x^2_2$$
So we have
$$\dot{V}=(-2\alpha^2+\frac{\alpha}{\beta}\sqrt{\alpha^2+\beta^2})x_1^2+(-2\beta^2+\frac{\beta}{\alpha}\sqrt{\alpha^2+\beta^2})x^2_2$$
Since $x_1^2>0$ and $x_2^2>0$
$$\begin{cases}-2\alpha^2+\frac{\alpha}{\beta}\sqrt{\alpha^2+\beta^2}<0\\-2\beta^2+\frac{\beta}{\alpha}\sqrt{\alpha^2+\beta^2}<0\end{cases}$$
$$2\alpha\beta>\sqrt{\alpha^2+\beta^2}$$

### (b)

The system stops moving at the equilibrium points 
$$\begin{cases}\dot{x}_1=-2x_1+x_1(x_1^2+x_2^2)=0\\\dot{x}_2=-x_2+x_2(x_1^2+x_2^2)=0\end{cases}$$
+ If $x_1=0$ and $x_2=0$, the origin $x=[0,0]^T$ is an equilibrium point
+ If $x_1=0$ and $x_2\neq0$, $x_2=\pm 1$
+ If $x_1\neq 0$ and $x_2=0$, $x_1=\pm\sqrt{2}$
+ If $x_1\neq 0$ and $x_2\neq0$, no possible solution

So the equilibrium points are $[0,0]^T$, $[0, 1]^T$, $[0,-1]^T$, $[\sqrt{2},0]^T$, $[-\sqrt{2},0]^T$

Linearize the system at origin $[0,0]^T$
$$\dot{x}=f(x)\approx f(0)+f'(0)x=\begin{bmatrix}\frac{\mathrm{d}\dot{x}_1}{\mathrm{d}x_1}&\frac{\mathrm{d}\dot{x}_1}{\mathrm{d}x_2}\\\frac{\mathrm{d}\dot{x}_2}{\mathrm{d}x_1}&\frac{\mathrm{d}\dot{x}_2}{\mathrm{d}x_2}\end{bmatrix}|_{x=0}\begin{bmatrix}x_1\\x_2\end{bmatrix}=\begin{bmatrix}-2&0\\0&-1\end{bmatrix}\begin{bmatrix}x_1\\x_2\end{bmatrix}$$
Since the linearized system at the origin has two strictly negative eigenvalue, the original nonlinear system is locally asymtotically stable at the origin.

The Lyapunov function of the nonlinear system can be chosen as
$$V(x)=\frac{1}{2}(x_1^2+x_2^2)>0$$
The sign of the derivative can be used to estimate the domain of attraction ($r^2=x_1^2+x_2^2$)
$$\begin{align}\dot{V}(x)=x_1\dot{x}_1+x_2\dot{x}_2=(x_1^2+x_2^2)^2-(2x_1^2+x_2^2)&\leq0\\(r^2)^2&\leq r^2+x_1^2\end{align}$$
+ When $x_1=0$, the inequation has $|x_2|\leq1$
+ When $x_2=0$, the inequation has $|x_1|\leq 1$

So the domain of attraction may be $||r||\leq 1$



---
## Question 4

### (a)

The system is controllable and observable if both the controllable matrix and the observable matrix have full rank $n=3$
$$\mathrm{det}(W_C)=\begin{vmatrix}B&AB&A^2B\end{vmatrix}=\begin{vmatrix}0&-a&-4a\\0&0&0\\a&3a&8a\end{vmatrix}\equiv0$$

$$\begin{align}\mathrm{det}(W_O)=\begin{vmatrix}C\\CA\\CA^2\end{vmatrix}=\begin{vmatrix}1&-1&b\\b+1&1-4b&3b-1\\4b&7-14b&8b-4\end{vmatrix}=2b^3-5b^2+4b-1&=0\\(b-0.5)(b-1)^2&=0\end{align}$$

The equation shows that: 
+ **Controllability** - the system is always uncontrollable regardless of $a$ since the second state variable can not be controlled by the input $u$
+ **Observability** - the system is observable when $b\neq1$ and $b\neq\frac{1}{2}$

### (b)

The rank of the controllability matrix is zero, meaning the systeom is not controllable
$$\mathrm{det}(W_C)=\begin{vmatrix}B&AB&A^2B&A^3B\end{vmatrix}=\begin{vmatrix}0&1&6&28\\1&2&4&8\\-1&-4&-16&-64\\1&3&10&36\end{vmatrix}=0$$
The transform matrix can be chosen as 
$$T=\begin{bmatrix}B&AB&e_1&e_2\end{bmatrix}=\begin{bmatrix}0&1&1&0\\1&2&0&1\\-1&-4&0&0\\1&3&0&0\end{bmatrix}$$
$$\bar{A}=T^{-1}AT=\begin{bmatrix}0&0&3&4\\0&0&-1&-1\\1&0&1&1\\0&1&-1&-2\end{bmatrix}\begin{bmatrix}5&1&1&1\\1&2&1&1\\-2&0&2&-2\\-1&-1&-1&3\end{bmatrix}\begin{bmatrix}0&1&1&0\\1&2&0&1\\-1&-4&0&0\\1&3&0&0\end{bmatrix}=\begin{bmatrix}0&-8&-10&-4\\1&6&3&1\\0&0&2&0\\0&0&5&4\end{bmatrix}$$
$$\bar{B}=T^{-1}B=\begin{bmatrix}1\\0\\0\\0\end{bmatrix}$$
The controllable and uncontrollable blocks are
$$A_c=\begin{bmatrix}0&-8\\1&6\end{bmatrix}$$
$$A_u=\begin{bmatrix}2&0\\5&4\end{bmatrix}$$

---
## Question 5

Since the matrix is uncontrollable, the closed-loop poles can not be settled at any location.
$$\mathrm{det}(W_C)=\begin{vmatrix}B&AB&A^2B\end{vmatrix}=\begin{vmatrix}0&1&-2\\1&-1&2\\0&1&-2\end{vmatrix}\equiv0$$
Calculate the characteristic polynomial of the closed-loop state matrix
$$\dot{x}=Ax+Bu=Ax+B(-Kx+r)=(A-BK)x+Br$$
$$\begin{align}\mathrm{det}(A-BK-\lambda I)&=\begin{vmatrix}-1-\lambda&1&0\\-k_1&-1-k_2-\lambda&1-k_3\\0&1&-1-\lambda\end{vmatrix}\\&=-\lambda^3-(k_2+3)\lambda^2+(k_1-2k_2-k_3-2)\lambda-(k_1+k_2+k_3)\end{align}$$
$$-\lambda^3-(k_2+3)\lambda^2+(k_1-2k_2-k_3-2)\lambda-(k_1+k_2+k_3)=(\lambda+2)(\lambda+1-j)(\lambda+1-j)$$
The characteristic polynomial should match the desired one, however, the coefficient of $\lambda^3$ of the left and right is not equal, thus the pole placement is not possible.

---

![](assignment_ls.pdf)