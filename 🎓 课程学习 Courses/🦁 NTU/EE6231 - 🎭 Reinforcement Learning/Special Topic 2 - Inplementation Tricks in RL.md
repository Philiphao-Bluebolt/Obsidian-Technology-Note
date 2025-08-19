Some implementation methods are hard to rigously explain in maths. They're usually just code-level optimization based on experience, which known as **tricks**

+ Part 1 doesn't introduce any trick since optimization by BE and BOE are mathematically rigous

+ **Part 2 - Tabular Sampling**
	+ [Sample-based Value Estimation](#Sample-based%20Value%20Estimation)
+ **Part 3 - Function Approximation**
	+ [Behavior SSD for Target PEV](#Behavior%20SSD%20for%20Target%20PEV)


+ **Part 4 - Neural Network**


---
## Sample-based Value Estimation

In model-based methods, value estimation is achieved by solving the BE(policy iteration) or BOE(value iteration), which both require a transition and reward probability model of the environment. 

However, most of the time we don't have access to the actual environment model and thus don't have BE or BOE at all.

+ **Tricks** - update the estimated value by **sampled return** instead using Monte-Carlo or temporal difference methods



---
## Behavior SSD for Target PEV

In the **off-policy** value approximation part, the objective function $J(w)$ in designed to describe the mean square error of the **target policy** value. Thus, it's intuitive that the error expectation should be weighted by the target policy stationary state distribution $d_\pi(s)$
$$\begin{align}J(w)&=\mathbb{E}_{s\sim d_b}[\frac{d_\pi(s)}{d_b(s)}(v_\pi(s)-V_\pi(s;w))^2]\\&=\mathbb{E}_{s\sim d_\pi}[(v_\pi(s)-V_\pi(s;w))^2]\end{align}$$
However, the SSD $d_\pi(s)$ of the **target policy** is hard to estimate since we only use the behavior policy in training. We don't really know which states are more tended to be visited under the target policy. 

+ **Tricks** - directly replace the target SSD weight with the **behavior SSD** in actual algorithms
$$J(w)=\mathbb{E}_{s\sim d_b}[(v_\pi(s)-V_\pi(s;w))^2]$$

---
## 