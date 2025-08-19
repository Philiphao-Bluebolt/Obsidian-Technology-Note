+ **Aim** - Simplify the analysis and synthesis of DTCS (Discrete Time Continuous Signal)
+ **What it does** -  $x(k)$ (Discrete time sequence) --> $X(z)$ (Complex Frequency-domain Representation)

+ [[#Definition]]
+ [[#Property]]
+ [[#Understanding]]
+ [[#Inverse Z Transform]]
	+ [[#Long Division Method]]
	+ [[#Computational Method]]
		+ [[#Matlab Approach]]
		+ [[#Difference Equation Approach]]
	+ [[#Partial Fraction Expansion (PFE) Method]]
	+ [[#Inversion Integral Method]]
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

There are a few approaches to do the Inverse Z Transform. Only some of the methods will return a closed-form result of the sequence.

+ No closed-form Result (Numerical)
	+ [[#Long Division Method]]
	+ [[#Computational Method]]
		+ [[#Matlab Approach]]
		+ [[#Difference Equation Approach]]
+ Closed-form Result (Analytic)
	+ [[#Partial Fraction Expansion (PFE) Method]]
	+ [[#Inversion Integral Method]]

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
The disadvantage of this method is method is obvious. Actually, we can't compute the **closed-form expression** of $x(k)$. The only things we get are some of the values at the front of the sequence.

### Computational Method

The discrete transfer function describes the relationship between the input and output signal of a discrete system.
$$\frac{Y(z)}{X(z)}=H(z)$$
Obviously, if the input $X(z)=1$, then the form of the system's transfer function will be the same as the output signal's Z transform. 
$$Y(z)=H(z) \quad $$
The unit sample function has a Z transform $X(z)=1$
$$x(k)=\begin{cases}1 & k=0\\0 & k\neq0\end{cases}$$
With this property, we can compute the output sequence $h(k)$ using system analysis software like Matlab.

#### Matlab Approach

To obtain the sequence of output $y(k)$, we use the `filter()` function

Here are the code:

```matlab
num = [1, 3, 1]
den = [1, 7, 2, 1]

x = [1, zeros(1, 40)]
y = filter(num, den, x)
```


#### Difference Equation Approach

We can still use Computational Method without a computer by reobtaining the original Difference Equation in the time domain using **Shifting Theorem**

Suppose we have a transfer function:
$$\frac{Y(z)}{X(z)}=\begin{align}H(z)&=\frac{1+3z^{-1}+z^{-2}}{1+7z^{-1}+2z^{-2}+z^{-3}}\\
\end{align}$$
The Difference Equation is:
$$
x(k)+3x(k-1)+x(k-2)=y(k)+7y(k-1)+2y(k-2)+y(k-3)
$$
Remember we use **unit sample function** as input
$$x(k)=\begin{cases}1 & k=0\\0 & k\neq0\end{cases}$$
Then we put the values of $x(k)$ into the Difference Equation, gradually calculate the each values of the output sequence $y(k)$
$$\begin{align}x(0)+3x(-1)+x(-2)&=y(0)+7y(-1)+2y(-2)+y(-3)\\
y(0)&=1\end{align}$$
$$\begin{align}x(1)+3x(0)+x(-1)&=y(1)+7y(0)+2y(-1)+y(-2)\\
y(1)&=-4\end{align}$$
$$...$$
The disadvantage of Computational Method is similar to Long Division Method. Instead of getting the whole closed-form expression, we only get a few values of the original sequence.

We need methods that can compute a closed-form result.


### Partial Fraction Expansion (PFE) Method

The concept of this method is simple. We expand the fraction-form Z transform into the sum of simpler fraction terms, then look up the Z transform table for the result.

The universal (causal) fraction-form Z transform is given by
$$X(z)=\frac{b_0z^m+b_1z^{m-1}+b_2z^{m-2}+...+b_m}{z^n+b_1z^{n-1}+b_2z^{n-2}+...+b_n} \quad m\leq n$$
Then, we compute the poles $\{p_1,p_2,..,p_n\}$ of $X(z)$. The fraction decomposite will be based on the poles.
$$z^n+b_1z^{n-1}+b_2z^{n-2}+...+b_n=0$$




### Inversion Integral Method

This method is based on the residue theory of complex function. 

> [!WARNING] The calculation here uses the function $X(z)z^{k-1}$ instead of $X(z)$ , which means that $m$ is the number poles in $X(z)z^{k-1}$, not $X(z)$ 

 The original sequence of $X(z)$ is given by the following expression in which $m$ is the number of poles in $X(z)z^{k-1}$ and $q$ is the order of current pole.
$$x(k)=\sum_{i=0}^m K_i=\frac{1}{(q-1)!} \lim_{z\to z_i } \frac{d^{q-1}}{dz^{q-1}}(z-z_i)^qX(z)z^{k-1}$$
If the pole $z_i$ is just a simple first order pole, then the expression could be simplified into the following form.
$$K_i=\lim_{z\to z_i}(z-z_i)X(z)z^{k-1}$$

---
## Solving Difference Equations

Z transform can be used to solve difference equations. 

The process is quiet simple, just transform the difference equation into Z transform and do a inverse transform, then you will get the closed-form expression of the sequence.