
+ **Notes**

+ **Lectures**
	+ [Lec 5](#Lec%205) - Monte Carlo Methods
	+ [Lec 6](#Lec%206) - Stochastic Approximation
	+ [Lec 7](#Lec%207) - Temporal-Difference Methods


---
## Monte Carlo Methods



---
## Stochastic Approximation

Stochastic Approximation is the fundamental of TD (temporal difference ) learning.

> **Mean Estimation** - the mean of random variable $X$ can be estimated by averaging a set of its **iid** (independent and identical distributed) samples $\{x_i\}_{i=1}^N$. The estimation is more accurate with a larger sample base $N$
$$\mathbb{E}(X)=\lim_{N\to\infty}\bar{x}=\lim_{N\to\infty}\frac{1}{N}\sum_{i=1}^N x_i\quad \quad x_i\sim X$$

There're two ways to calculate the mean estimation, either collecting all the samples and doing a one-time calculation or calculation incrementally when new samples come in. The letter one is appreciated for its practicability.

> **Incremental Estimation** - the mean estimation $w_k$ is iteratively updated when receiving a new sample $x_k$
$$\begin{align}w_{k+1}&=\frac{1}{k}\sum_{i=1}^k x_i\\&=\frac{1}{k}(\sum_{i=1}^{k-1} x_i+x_k)\\&=\frac{k-1}{k}(\frac{1}{k-1}\sum_{i=1}^{k-1}x_i+\frac{x_k}{k-1})\\&=\frac{k-1}{k}(w_k+\frac{x_k}{k-1})\\&=w_k-\frac{1}{k}(w_k-x_k)\end{align}$$












---
## Questions

> **(Lec 5) What is the difference between first visit MC and every visit MC?**

If a state $s$ is visited multiple times in a episode, the first visit MC will only consider the return from the first visit while every visit MC will consider the return of every visit.

> **(Lec 6) Why is the Monte-Carlo method a offline algorithm? Can't we dynamically update the average just like TD?**

Monte-Carlo is not necessary a offline algorithm. It can be programmed to update the estimation of action values at every step, which makes it online.

> **(Lec 7) Why does the TD uses next Q value to update the current Q value? Usually Q value is defined as the expectation of the next V value over the returns**

Although this update method is not intuitive by definition, it's actually practical to do so. The transition between states can be viewed as a graph where states are nodes and actions are links. Since the current state-action pair $(S_t,A_t)$ leads to a few next states and a state value $v_\pi(S_{t+1})$ is defined as the average over all its possible action values, updating the current action value by the next action value actually "gives credit to" the current action **link**.

> **(Lec 7) Is the Bellman Equation used in the sampling-based methods?**

Although the sampling-based value evulation equation doesn't look like the Bellman Equation in forms, they're directly


---
## Slides


### Lec 5

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%205(3).pdf)


### Lec 6

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%206(1).pdf)


### Lec 7

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%207(2).pdf)

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%207b.pdf)


