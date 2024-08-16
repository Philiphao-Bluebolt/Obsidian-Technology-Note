+ **Aim** - Simplify the analysis and synthesis of DTCS (Discrete Time Continuous Signal)
+ **What it does** -  $x(k)$ (Discrete time series) --> $X(z)$ (Complex Frequency-domain Representation)

+ [[#Definition]]
+ [[#Property]]
+ [[#Understanding]]

---
## Definition

One-sided Form (Sum starts from 0) is more widely used because only positive time is considered
$$X(z)=Z\{x(t)\}=\sum_{k=0}^{\infty}x(kT)z^{-k}$$
$T$ - sampling period
$k$ - number of sample ($k=0,1,2,...$)

The difference between One-sided Form $\sum_{k=0}^\infty$ and Two-sided Form $\sum_{-\infty}^\infty$


---
## Property

1. Multiplication by a constant
$$Z\{ax(t)\}=aZ\{x(t)\}=aX(z)$$
2. Linearity
$$Z\{af(t)+bg(t)\}=aZ\{f(t)\}+bZ\{g(t)\}=aF(z)+bG(z)$$
3. Multiplication by a exponential of $k$
$$Z\{a^kx(t)\}=X(a^{-1}z)$$
4. Shifting Theorem - Delay  ($x(t)=0$ for $t<0$)
$$Z\{x(t-nT)\}=z^{-n}X(z)$$
5. Shifting Theorem - Advance  ($x(t)=0$ for $t<0$)
$$Z\{x(t+nT)\}=z^n[X(z)-\sum^{n-1}_{k=0}x(kT)z^{-k}]$$
6. Complex Translation Theorem
$$Z\{e^{-at}x(t)\}=X(ze^{aT})$$
7. Initial Value Theorem  ($\lim_{z\to\infty}X(z)$ must exist)
$$x(0)=\lim_{z\to\infty}X(z)$$
8. Final Value Theorem  (All poles of $X(z)$ must be inside the unit circle)
$$\lim_{k\to\infty}x(k)=\lim_{z\to1}(1-z^{-1})X(z)$$
---
## Understanding

+ Video - [Understanding the Z-Transform](https://www.youtube.com/watch?v=XJRW6jamUHk)

