ZHENG ZHENHAO - G2402550D

+ Q1 - [Direct Synthesis Method (DSM)](#Direct%20Synthesis%20Method%20(DSM))
	1. [PID Controller Design](#PID%20Controller%20Design)
	2. [Response Simulation](#Response%20Simulation)
+ Q2 - [Internal Model Control (IMC) with 1 DoF](#Internal%20Model%20Control%20(IMC)%20with%201%20DoF)
	1. [IMC Controller Design](#IMC%20Controller%20Design)
	2. [Standard PID Controller Design](#Standard%20PID%20Controller%20Design)
	3. [Response Simulation](#Response%20Simulation)
+ Q3 - [Internal Model Control (IMC) with 2 DoF](#Internal%20Model%20Control%20(IMC)%20with%202%20DoF)
	1. [IMC Controller Design and Simulation 1](#IMC%20Controller%20Design%20and%20Simulation%201)
	2. [IMC Controller Design and Simulation 2](#IMC%20Controller%20Design%20and%20Simulation%202)
	3. [Response Comparison](#Response%20Comparison)
+ Q4 - [Cascade Structure and Feedforward Control](#Cascade%20Structure%20and%20Feedforward%20Control)
	1. [Cascade Structure and Feedforward Control](#Cascade%20Structure%20and%20Feedforward%20Control)
	2. [Cascade Controller with IMC 1](#Cascade%20Controller%20with%20IMC%201)
	3. [Cascade Controller with IMC 2](#Cascade%20Controller%20with%20IMC%202)
	4. [Feed-forward Controller](#Feed-forward%20Controller)
+ Q5 - [Automobile Cruise Control](#Automobile%20Cruise%20Control)
	1. [PID Controller Design for Velocity Control](#PID%20Controller%20Design%20for%20Velocity%20Control)
	2. [Simulation](#Simulation)


---
## Direct Synthesis Method (DSM)

### PID Controller Design

The unit feedback closed-loop transfer function
$$G_{cl}(s)=\frac{G_c(s)G(s)}{1+G_c(s)G(s)}$$
The controller transfer function can be calculated based on the desired closed-loop transfer function and the plant model ($e^{-s}\approx 1-s$)
$$\begin{align}G_c(s)&=\frac{1}{G(s)}\frac{G_{cld}(s)}{1-G_{cld}(s)}\\&=\frac{(5s+1)(2s+1)}{2e^{-s}}\frac{\frac{e^{-s}}{\tau_cs+1}}{1-\frac{e^{-s}}{\tau_cs+1}}\\&=\frac{(5s+1)(2s+1)\cancel{e^{-s}}}{2\cancel{e^{-s}}(\tau_cs+1-e^{-s})}\\&=\frac{(5s+1)(2s+1)}{2(\tau_c+1)s}\end{align}$$
+ The PID controller when $\tau_c=1\mathrm{s}$
$$G_c(s)=\frac{(5s+1)(2s+1)}{4s}=\frac{7}{4}(1+\frac{1}{7s}+\frac{10s}{7})$$
+ The PID controller when $\tau_c=10\mathrm{s}$
$$G_c(s)=\frac{(5s+1)(2s+1)}{22s}=\frac{7}{22}(1+\frac{1}{7s}+\frac{10s}{7})$$

### Response Simulation

The disturbance closed-loop transfer function ($e^{-\theta}\approx 1-\theta s$)
$$\begin{align}\frac{Y(s)}{D(s)}&=\frac{G_d(s)}{1+G_c(s)G(s)}\\&=\frac{e^{-0.5s}}{(10s+1)(5s+1)}\frac{1}{1+\frac{(5s+1)(2s+1)}{2(\tau_c+1)s}\frac{2e^{-s}}{(5s+1)(2s+1)}}\\&=\frac{1-0.5s}{(10s+1)(5s+1)}\frac{(\tau_c+1)s}{1+\tau_cs}\end{align}$$

The output $Y(s)$ is described as
$$\begin{align}Y(s)&=\frac{Y(s)}{R(s)}R(s)+\frac{Y(s)}{D(s)}D(s)\\&=\frac{e^{-s}}{\tau_cs+1}\frac{1}{s}+\frac{1-0.5s}{(10s+1)(5s+1)}\frac{(\tau_c+1)s}{1+\tau_cs}\frac{e^{-60s}}{s}\end{align}$$
Apply a unit step reference input at $t=0\mathrm{s}$ and a unit step disturbance at $t=60\mathrm{s}$
![](Pasted%20image%2020250420231356.png)

+ The output response $y(t)$ when $\tau_c=1\mathrm{s}$

![](Pasted%20image%2020250420231238.png)

+ The output response $y(t)$ when $\tau_c=10\mathrm{s}$

![](Pasted%20image%2020250420231143.png)


---
## Internal Model Control (IMC) with 1 DoF

### IMC Controller Design

The plant model can be factorized into two parts and one of them should include all the RHP zeros and pure delays
$$\tilde{G}(s)=\frac{2(-s+1)}{(5s+1)(2s+1)}=(-s+1)\frac{2}{(5s+1)(2s+1)}$$
$$\tilde{G}_+(s)=-s+1\quad\quad\tilde{G}_-(s)=\frac{2}{(5s+1)(2s+1)}$$
Then the IMC controller is derived by the following formula
$$G_c^*(s)=\frac{1}{\tilde{G}_-(s)}f=\frac{(5s+1)(2s+1)}{2(\tau_cs+1)}=\frac{2s+1}{2}$$
### Standard PID Controller Design

The standard PID controller is calculated by
$$G_c(s)=\frac{G_c^*(s)}{1-G_c^*(s)\tilde{G}(s)}=\frac{\frac{2s+1}{2}}{1-\frac{\cancel{2s+1}}{\cancel{2}}\frac{\cancel{2}(-s+1)}{(5s+1)\cancel{(2s+1)}}}=\frac{(2s+1)(5s+1)}{12s}$$
The PID parameters can be obtained by substitution
$$G_c(s)=K_c(1+\frac{1}{\tau_Is}+\tau_Ds)=\frac{(2s+1)(5s+1)}{12s}=\frac{7}{12}(1+\frac{1}{7s}+\frac{10s}{7})$$
$$K=\frac{7}{12}\quad\quad\tau_I=7\quad\quad\tau_D=\frac{10}{7}$$
Using DSM to design the standard controller for comparison
$$G_{cld}(s)=\tilde{G}_+(s)f=\frac{-s+1}{5s+1}$$
$$\begin{align}G_c(s)&=\frac{1}{G(s)}\frac{G_{cld}(s)}{1-G_{cld}(s)}\\&=\frac{(5s+1)(2s+1)}{2(-s+1)}\frac{\frac{-s+1}{5s+1}}{1-\frac{-s+1}{5s+1}}\\&=\frac{(5s+1)(2s+1)}{12s}\end{align}$$
It shows that when the plant is **perfectly modelled** as $\tilde{G}(s)=G(s)$, the standard controllers designed by the IMC and DSM are identical

### Response Simulation

Since the plant is **perfectly modelled**, the output $Y(s)$ is described as 
$$\begin{align}Y(s)&=G_c^*(s)G(s)R(s)+(1-G_c^*(s)G(s))G_d(s)D(s)\\&=\frac{2s+1}{2}\frac{2(-s+1)}{(5s+1)(2s+1)}\frac{1}{s}+(1-\frac{2s+1}{2}\frac{2(-s+1)}{(5s+1)(2s+1)})\frac{e^{-s}}{(10s+1)(5s+1)}\frac{e^{-60s}}{s}\\&=\frac{1-s}{5s+1}\frac{1}{s}+\frac{6\cancel{s}e^{-s}}{(5s+1)^2(10s+1)}\frac{e^{-60s}}{\cancel{s}}\\&=\frac{1-s}{s(5s+1)}+\frac{6e^{-61s}}{(5s+1)^2(10s+1)}\end{align}$$
Apply a unit step reference input at $t=0\mathrm{s}$ and a unit step disturbance at $t=60\mathrm{s}$

![](Pasted%20image%2020250420231830.png)

![](Pasted%20image%2020250420231808.png)


---
## Internal Model Control (IMC) with 2 DoF

### IMC Controller Design and Simulation 1

Firstly, factorize the plant model 
$$\tilde{G}(s)=\tilde{G}_+(s)\tilde{G}_-(s)=\frac{e^{-2s}}{10s+1}=e^{-2s}\frac{1}{10s+1}$$
$$\tilde{G}_+(s)=e^{-2s}\quad\quad\tilde{G}_-(s)=\frac{1}{10s+1}$$
The IMC controller is given by $\tau_c=2, r=1, \lambda=0$
$$G_c^*(s)=\frac{1}{\tilde{G}_-(s)}f=(10s+1)\frac{\lambda s+1}{(\tau_c s+1)^r}=\frac{10s+1}{2s+1}$$
Since the plant model is considered precise, the output $Y(s)$ is given by
$$\begin{align}Y(s)&=\frac{Y(s)}{R(s)}R(s)+\frac{Y(s)}{D(s)}D(s)\\&=G(s)G_s(s)R(s)+(1-G_c^*(s)\tilde{G}(s))G_d(s)D(s)\\&=\frac{e^{-2s}}{10s+1}\frac{1}{s}+(1-\frac{10s+1}{2s+1}\frac{e^{-2s}}{10s+1})\frac{e^{-2s}}{10s+1}\frac{e^{-20s}}{s}\\&=\frac{e^{-2s}}{s(10s+1)}+\frac{e^{-22s}}{(10s+1)s}-\frac{e^{-24s}}{s(10s+1)(2s+1)}\end{align}$$
Apply a unit step reference input at $t=0\mathrm{s}$ and a unit step disturbance at $t=20\mathrm{s}$

![](Pasted%20image%2020250420233318.png)

![](Pasted%20image%2020250420233006.png)

### IMC Controller Design and Simulation 2

$\lambda$ is given by the following equation with $s=-\frac{1}{10}$, which is the pole of the $G_d(s)$ function
$$\begin{align}[1-G(s)G^*_c(s)]|_{s=-\frac{1}{10},\tau_c=2,r=2}&=0\\ [1-\frac{e^{-2s}}{10s+1}(10s+1)\frac{\lambda s+1}{(\tau_cs+1)^r}]|_{s=-\frac{1}{10},\tau_c=2,r=2}&=0\\\lambda&=4.76\end{align}$$
The IMC controller is given by $\tau_c=2, r=2, \lambda=4.76$
$$G_c^*(s)=\frac{1}{\tilde{G}_-(s)}f=(10s+1)\frac{\lambda s+1}{(\tau_c s+1)^r}=\frac{(10s+1)(4.76s+1)}{(2s+1)^2}$$
The output $Y(s)$ is given by the following equation
$$\begin{align}Y(s)&=\frac{Y(s)}{R(s)}R(s)+\frac{Y(s)}{D(s)}D(s)\\&=G(s)G_s(s)R(s)+(1-G_c^*(s)\tilde{G}(s))G_d(s)D(s)\\&=\frac{e^{-2s}}{10s+1}\frac{1}{\tau_ss+1}\frac{1}{s}+(1-\frac{(10s+1)(4.76s+1)}{(2s+1)^2}\frac{e^{-2s}}{10s+1})\frac{e^{-2s}}{10s+1}\frac{e^{-20s}}{s}\end{align}$$
 $\tau_s=1$ is chosen

Apply a unit step reference input at $t=0\mathrm{s}$ and a unit step disturbance at $t=20\mathrm{s}$

![](Pasted%20image%2020250420232659.png)

![](Pasted%20image%2020250420232639.png)

### Response Comparison

Since the $\lambda$ is carefully chosen, the output response with the second controller is less sensative to disturbance and has a smaller settling time. However, the initial reference step response is nearly identical.

---
## Cascade Structure and Feedforward Control

### Cascade Controller with IMC 1

Firstly, factorize inner plant $p_2(s)$
$$p_2(s)=\frac{2e^{-4s}}{s+1}\quad\quad p_{2+}(s)=e^{-4s}\quad\quad p_{2-}(s)=\frac{2}{s+1}$$
The inner controller $q_2(s)$ is given by
$$q_2(s)=\frac{f_2}{p_{2-}}=\frac{s+1}{2}\frac{1}{4s+1}=\frac{s+1}{8s+2}$$
Then, factorize the whole plant $p_1(s)$
$$p(s)=p_1(s)p_2(s)=\frac{e^{-20s}}{15s+1}\frac{2e^{-4s}}{s+1}=\frac{2e^{-24s}}{(15s+1)(s+1)}$$$$ p_{+}(s)=e^{-24s}\quad\quad p_{-}(s)=\frac{2}{(15s+1)(s+1)}$$The outer controller $q_1(s)$ is given by
$$q_1(s)=\frac{f_1}{p_{1-}}=\frac{15s+1}{(18s+1)^2}=\frac{(15s+1)(s+1)}{2(18s+1)^2}$$
Apply a unit step reference input at $t=0\mathrm{s}$ and a unit step disturbance $d_1$ at $t=40\mathrm{s}$

![](Pasted%20image%2020250421110838.png)

![](Pasted%20image%2020250421110820.png)

### Cascade Controller with IMC 2

The outer controller is the same as part 1
$$q_1(s)=\frac{(15s+1)(s+1)}{2(18s+1)^2}$$
The inner controller $\lambda$ is given by
$$\begin{align}[1-p_2(s)\frac{1}{p_{2-}(s)}\frac{\lambda s+1}{(4s+1)^2}]|_{s=-\frac{1}{15}}&=0\\ [1-\frac{2e^{-4s}}{s+1}\frac{s+1}{2}\frac{\lambda s+1}{(4s+1)^2}]|_{s=-\frac{1}{15}}&=0\\\lambda&=8.82\end{align}$$
The inner controller $q_2(s)$ is given by
$$q_2(s)=\frac{f_2}{p_{2-}}=\frac{s+1}{2}\frac{\lambda s+1}{(4s+1)^2}=\frac{(s+1)(8.82s+1)}{2(4s+1)^2}$$
Apply a unit step reference input at $t=0\mathrm{s}$ and a unit step disturbance $d_1$ at $t=40\mathrm{s}$

![](Pasted%20image%2020250421111029.png)

![](Pasted%20image%2020250421111011.png)

### Feed-forward Controller

The feed-forward Controller can be obtained by
$$q_{ff}(s)=p_{2-}^{-1}p_{1-}^{-1}(s)g_{d-}(s)=\frac{s+1}{2}\frac{15s+1}{(10s+1)(0.3s+1)}=\frac{(15s+1)(s+1)}{2(10s+1)(0.3s+1)}$$
Apply a unit step reference input at $t=0\mathrm{s}$ and a unit step disturbance $d_1$ at $t=40\mathrm{s}$

![](Pasted%20image%2020250421112817.png)

![](Pasted%20image%2020250421112801.png)

### Response Comparison

The system returns to state space faster with the feed-forward controller

---
## Automobile Cruise Control

### PID Controller Design for Velocity Control

We use IMC to obtain the controller assuming $\tilde{G}(s)=G(s)$

Firstly, factorize the vehicle model and choose the $f$ function
$$\tilde{G}(s)=\frac{0.001}{s+0.05}=\tilde{G}_-(s)\quad\quad\tilde{G}_+(s)=0$$
$$f= \frac{1}{(\tau_ss+1)^r}$$
The IMC controller is given by
$$G^*_c(s)=\frac{1}{\tilde{G}_-(s)}f=\frac{s+0.05}{0.001(\tau_ss+1)^r}$$
The standard IMC is given by
$$G_c(s)=\frac{G^*_c(s)}{1-G^*_c(s)\tilde{G}(s)}=\frac{\frac{s+0.05}{0.001(\tau_ss+1)^r}}{1-\frac{s+0.05}{0.001(\tau_ss+1)^r}\frac{0.001}{s+0.05}}=\frac{s+0.05}{0.001[(\tau_ss+1)^r-1]}$$
After tuning the parameters $r=2$ and $\tau_s=0.3$, the PID controller is given as
$$G_c(s)=\frac{s+0.05}{0.00009s^2+0.0006s}$$
### Simulation

![](Pasted%20image%2020250420225534.png)

![](Pasted%20image%2020250420225501.png)



---
## Slide

![](EE%206225_Assignment1_020425%20(1).pdf)