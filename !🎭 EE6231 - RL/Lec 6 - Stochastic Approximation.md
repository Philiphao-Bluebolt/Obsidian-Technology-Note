Stochastic Approximation is the fundamental of TD (temporal difference ) learning.

> **Mean Estimation** - the mean of random variable $X$ can be estimated by averaging a set of its **iid** (independent and identical distributed) samples $\{x_i\}_{i=1}^N$. The estimation is more accurate with a larger sample base $N$
$$\mathbb{E}(X)=\lim_{N\to\infty}\bar{x}=\lim_{N\to\infty}\frac{1}{N}\sum_{i=1}^N x_i\quad \quad x_i\sim X$$

There're two ways to calculate the mean estimation, either collecting all the samples and doing a one-time calculation or calculation incrementally when new samples come in. The letter one is appreciated for its practicability.

> **Incremental Estimation** - the mean estimation $w_k$ is iteratively updated when receiving a new sample $x_k$
$$\begin{align}w_{k+1}&=\frac{1}{k}\sum_{i=1}^k x_i\\&=\frac{1}{k}(\sum_{i=1}^{k-1} x_i+x_k)\\&=\frac{k-1}{k}(\frac{1}{k-1}\sum_{i=1}^{k-1}x_i+\frac{x_k}{k-1})\\&=\frac{k-1}{k}(w_k+\frac{x_k}{k-1})\\&=w_k-\frac{1}{k}(w_k-x_k)\end{align}$$






---
## Slide
