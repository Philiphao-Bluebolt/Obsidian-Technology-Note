+ **Aim** - Simplify the analysis and synthesis of DTCS (Discrete Time Continuous Signal)
+ **What it does** -  $x(k)$ (Discrete time sequence) --> $X(z)$ (Complex Frequency-domain Representation)

+ [[#Definition]]
+ [[#Property]]
+ [[#Understanding]]
+ [[#Inverse Z Transform]]
	+ [[#Long Division Method]]
	+ [[#Difference Equation Approach]]
+ [[#Solving Difference Equations]]

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


---
## Inverse Z Transform

Inverse Z Transform is the reverse process of Z Tranform, it reobtains the **discrete** sequence $x(k)$ in time domain from its frequency domain
$$Z^{-1}\{X(z)\}=x(k)$$
Notice that the Inverse Z Transform can only calculate the sampled discrete $x(k)$ but not the original continuous form $x(t)$. The rebuild of the $x(t)$ would only be successful when the sampling period $T$ fulfills the **Nyquist–Shannon sampling theorem**

There are a few approaches to do the Inverse Z Transform.

| Methods                    | Advantages      | Disadvantages                    |
| -------------------------- | --------------- | -------------------------------- |
| Long Division              | Easy to compute | Can't get closed-form expression |
| Computational              |                 |                                  |
| Partial Fraction Expansion |                 |                                  |
| Inversion Integral         |                 |                                  |

### Long Division Method

Just inspect the form of the expanded Z Transform expression, the **coefficient of each term** of the series is one value of the original sequence in time domain.
$$Z\{x(k)\}=\sum_{k=0}^{\infty}x(k)z^{-k}=\color{magenta}x(0)\color{black}z^0+\color{magenta}x(1)\color{black}z^{-1}+\color{magenta}x(2)\color{black}z^{-2}+...$$
If we rewrites the Z Transform in the series form, we'll know each value of the original sequence. The transfer of **fraction form** Z Transform to the series form can be easily done by **Long Division**

An example here: 
$$\begin{align}Z\{x(k)\}&=\frac{1+3z^{-1}+z^{-2}}{1+7z^{-1}+2z^{-2}+z^{-3}}\\
\end{align}$$
Apply the long division to the fraction

![[c7838614a752db8970c3198b94620b2.jpg]]
And here we get the value for $x(0),x(1),x(2)$
$$x(k)=1-4z^{-1}+27z^{-2}+...$$
The disadvantage of this method is method is obvious. Actually, we can't compute the closed-form expression of $x(k)$. The only things we get are some of the values at the front of the sequence.

### Computational Method


### Partial Fraction Expansion


### Inversion Integral




---
## Solving Difference Equations