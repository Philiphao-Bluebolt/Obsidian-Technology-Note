+ **Goal** - Design a digital controller for a plant fulfilling the required output response

There're 3 ways to design a discrete time controller:

+ Obtain from Continuous System
	+ [[#System Discretization Method]]
		+ [[#Integral Approximation]]
		+ [[#Pole-Zero Matching]]
	+ [[#Frequency Response Design]]
+ Obtain Discrete System directly
	+ [[#Direct Closed‐loop Synthesis Design]]
		+ [[#Closed-loop Function Conditions]]
		+ [[#Deadbeat Controller Design]]
		+ [[#Ripple‐free Controller Design]]
+ [[#Other Controller Design Method]]
	+ 


---
## System Discretization Method

Discretization converts a continuous system into a discrete one.

### Integral Approximation

The idea of Integral Approximation is to operate integral on every period $(k-1)T \to kT$ of the time-domain equation and approximate the value of the integral to get the discrete differential equation for the digital controller. 

The approximate can be done by: 

+ Backward Difference Method
$$s=\frac{z-1}{Tz}$$
+ Forward Difference Method
$$s=\frac{z-1}{T}$$
+ Bilinear Transformation Method
$$s=\frac{2(z-1)}{T(z+1)}$$
The discrete control is stable if and only if its continuous counterpart is stable. 

A successful conversion means that the frequency response of the discrete system and continuous system under half the sampling angular frequency ${\omega_s}/{2}$ is highly identical.

### Pole-Zero Matching

For a continuous controller with $m$ zeros and $n$ poles, apply the following steps
$$G_a(s)=K\frac{\prod_{i=1}^m(s-z_i)}{\prod_{j=1}^n(s-p_j)}$$
+ Map all the zeros and poles from $s$ to $z$ using $z=e^{sT}$
+ Add $n-m-1$ zeros $(z+1)$
+ Obtain the new discrete gain $\alpha$ with $G(z=1)=G_a(s=0)$

After this, we obtain a digital representative of the original continuous controller
$$G(z)=\alpha\frac{(z+1)^{n-m-1}\prod_{i=1}^m(z-e^{z_iT})}{\prod_{j=1}^n(z-e^{p_jT})}$$

---
## Frequency Response Design




---
## Direct Closed‐loop Synthesis Design

+ Get controller $C(z)$ directly from a chosen closed-loop function $G_{cl}(z)$

If the complete closed-loop pulse transfer function can be determined by design specification, the controller function $C(z)$ can be directly derived by simple block diagram maths.

![[Pasted image 20241111105537.png]]
$$\begin{align}G_{cl}(z)&=\frac{C(z)G_{ZAS}(z)}{1+C(z)G_{ZAS}(z)}\\C(z)&=\frac{1}{G_{ZAS}(z)}\frac{G_{cl}(z)}{1-G_{cl}(z)}\end{align}$$
### Closed-loop Function Conditions 

When choosing a closed-loop function $G_{cl}(z)$, we have to ensure that the resulting $C(z)$ is causal and the system is stable. To achieve that, a few conditions should be fulfilled.

+ **Causality** - The relative degree (number of poles minus zeros) of $G_{cl}(z)$ should **not** be less than $G_{ZAS}(z)$
+ **Stability** - All the unstable or critical-stable poles and zeros (outside or on the unit circle) of $G_{ZAS}(z)$ should be cancelled out by $\frac{G_{cl}(z)}{1-G_{cl}(z)}$
+ **Zero Steady-state Error** - The final value theorem implys that $G_{cl}(z=1)=1$

### Finite Settling Time (Deadbeat Controller) Design

Deadbeat control brings the response to the steady state in the smallest number of time steps. It can be achieved by letting
$$G_{cl}(z)=z^{-k}\quad\quad k\in N^+$$
The number of poles $k$ should be no less than the relative degree of the discrete zero analog system $G_{ZAS}(z)$ to ensure causality.

Once implemented, deadbeat controller always has zero steady-state error, which can be proved by the final value theorem.
$$\lim_{z\to1}(1-z^{-1})G_{cl}(z)=\lim_{z\to1}(\frac{1}{z^k}-\frac{1}{z^{1+k}})=0$$
However, deadbeat control is not always stable as it can not always eliminate all the unstable poles and zeros from the controlled plant $G_{ZAS}(z)$.

Another drawback is that finite settling time design will result in large intersample oscillations.

### Ripple‐free Controller Design

Ripple‐free controller eliminates intersample oscillations produced by pure deadbeat control


---
## Other Controller Design Method

### One Degree of Freedom Controller



### Two Degree of Freedom Controller