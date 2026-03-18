The exercise focuses on Z tranform and discrete system. You can use a Z transform table for convenience.

+ Exercise 1
	+ [[#1-4 Z transform of a sum of sequence]]
	+ [[#1-5 Z transform of a piecewise function]]
+ Exercise 2
	+ [[#2-1 Inverse Z transform for a finite sequence]]
	+ [[#2-2 Inverse Z transform using Partial Fraction Expansion]]
	+ [[#2-3 Inverse Z transform and the initial and final value]]
	+ [[#2-4 Inverse Z transform using Inversion Integral Method]]
	+ [[#2-5 Inverse Z transform]]
+ Exercise 3
	+ 
+ Exercise 4

![[Exercises.pdf]]


---
## Exercise 1

#### 1-4  Z transform of a sum of sequence
$$y(k)=\sum_{h=0}^k a^h$$
Write down a few of the expression of $y(k)$
$$\begin{align}y(0)&=a^0\\
y(1)&=y(0)+a^1\\
y(2)&=y(1)+a^2\\
\end{align}$$
 you can catch the pattern that each value of $y(k)$ is the sum of its last value and $a^k$
$$y(k)=y(k-1)+a^k$$
Then operate Z transform on this new differential equation using the delay shifting property 
$$\begin{align}Y(z)&=z^{-1}Y(z)+\frac{1}{1-az^{-1}}\\
Y(z)&=\frac{1}{(1-az^{-1})(1-z^{-1})}\end{align}$$


#### 1-5  Z transform of a piecewise function 
$$x(t)=\begin{cases}0 &0\leq x<2\\\frac{x-2}{3} &2\leq x<5 \\ 1 & x\geq 5  \end{cases}$$
(Sampling period $T=1s$)

There's a dumb approach for this. That is, directly sum up and value before $x=5$ and treat the remain ones as a delayed unit function
$$\begin{align}X(z)&=(\frac{z^{-3}}{3}+\frac{2z^{-4}}{3})+z^{-5}+z^{-6}+...\\&=\frac{z^{-3}+2z^{-4}}{3}+\frac{z^{-4}}{z-1}\\&=\frac{z^{-3}+z^{-4}+z^{-5}}{3-3z^{-1}}\end{align}$$

---
## Exercise 2

#### 2-1  Inverse Z transform for a finite sequence
$$X(z)=\frac{1+2z+3z^2+4z^3+5z^4}{z^4}$$

The given expression can be written as
$$X(z)=5+4z^{-1}+3z^{-2}+2z^{-3}+z^{-4}$$
So the original sequence is
$$x(k)=\begin{cases}5-k&0\leq k\leq4\\0 & k>4\end{cases}$$

#### 2-2  Inverse Z transform using Partial Fraction Expansion
$$X(z)=\frac{z^{-1}(0.5-z^{-1})}{(1-0.5z^{-1})(1-0.8z^{-1})^2}$$

We decomposite the function into two rational fractions
$$X(z)=\frac{A}{1-0.5z^{-1}}+\frac{B+Cz^{-1}}{(1-0.8z^{-1})^2}$$
Solve the following equations to get constant $A,B,C$
$$\begin{cases}A+B=0\\
-1.6A-0.5B+C=0.5\\
0.64A-0.5C=-1\end{cases}$$
$$\begin{cases} A=-\frac{25}{3}\\B=\frac{25}{3} \\C=-\frac{26}{3}\end{cases}$$
Then we get
$$X(z)=-\frac{25}{3}\frac{1}{1-0.5z^{-1}}+\frac{}{}$$
#### 2-3  Inverse Z transform and the initial and final value
$$X(z)=\frac{z^{-1}}{(1-z^{-1})(1+1.3z^{-1}+0.4z^{-2})}$$



#### 2-4  Inverse Z transform using Inversion Integral Method
$$X(z)=\frac{1+z^{-1}-z^{-2}}{1-z^{-1}}$$

The function $X(z)z^{k-1}$ has two poles $\{0, 1\}$
$$X(z)z^{k-1}=\frac{z^2+z-1}{z(z-1)}\frac{z^k}{z}=\frac{z^{k}(z^2+z-1)}{z^2(z-1)}$$
The residue expression
$$\begin{align}x(k)&=\lim_{z\to1}(z-1)X(z)z^{k-1}+\frac{1}{(2-1)!}\lim_{z\to0}[\frac{d}{dz}z^2\frac{z^{k}(z^2+z-1)}{z^2(z-1)}]\\&=1+\lim_{z\to0}\frac{(k+1)z^{k+2}-(3k+3)z^{k+1}-2kz^k+kz^{k-1}}{(z-1)^2}\\&=\end{align}$$

#### 2-5  Inverse Z transform
$$X(z)=\frac{z^{-3}}{(1-z^{-1})(1-0.2z^{-1})}$$

+ Use Partial Fraction Expansion
$$\begin{align}X(z)&=z^{-3}(\frac{1.25}{1-z^{-1}}-\frac{0.25}{1-0.2z^{-1}})\\&=z^{-3}Z\{\frac{5-5^{-k}}{4}\}\end{align}$$
$$x(k)=\begin{cases}0 & 0\leq k <3 \\ \frac{5-5^{3-k}}{4} =1.25(1-0.2^{k-2}) & k\geq3\end{cases}$$

---
## Exercise 3

#### 3-1  Solve a differential equation with unit impulse

$$x(k+2)+2x(k+1)-x(k)=\delta(k) \quad x(k)=0\quad for  \quad k<0$$

First, transform the given equation to the Z domain. Shifting property is used here.
$$\begin{align}z^2[X(z)-x(0)-x(1)z^{-1}]+2z[X(z)-x(0)]-X(z)&=1\\(z^2+2z-1)X(z)-(z^2+2z)x(0)-zx(1)&=1\end{align}$$
Actually, we don't know the value of $x(0), x(1)$ here, so calculation must be done.
$$\begin{align}k&=-2 \quad x(0)+2x(-1)-x(-2)=\delta(-2)\\k&=-1 \quad x(1)+2x(0)-x(-1)=\delta(-1)\end{align}$$
Now we know that $x(0)=x(1)=0$
$$X(z)=\frac{1}{z^2+2z-1}$$
Next, compute the closed-form expression of $x(k)$
$$X(z)=\frac{1}{z^2+2z-1}=\frac{}{}$$


#### 3-2  Obtain Pulse transfer function from a laplace form
$$X(s)=\frac{s+3}{(s+2)(s+1)}$$
First we transform this back to the continuous signal
$$X(s)=\frac{s+3}{(s+2)(s+1)}=\frac{2}{s+1}-\frac{1}{s+2}$$
$$x(t)=2e^{-t}-e^{-2t}$$
Then sample the continuous signal and transform the discrete sequence into Z domain
$$X(z)=\frac{e^{3T}-2e^Tz^{-1}+e^{2T}z^{-1}}{(e^T-z^{-1})(e^{2T}-z^{-1})}$$

#### 3-3  