These examples mainly focuse on the calculation technique of Z transform and inverse transform

+ [[#Proof of Z Transform Properties]]
	+ [[#Shifting Theorem - Delay]]
	+ [[#Shifting Theorem - Advance]]
+ [[#Z Transform Calculation]]
	+ [[#2-1 Z Transform of Laplace Form Signal]]
	+ [[#2-2 Find the Z Transform of a delaying unit step]]
	+ [[#2-3 Obtain the Z Transform of a delayed exponential series]]
	+ [[#2-4 Represent the Z Transform of y(k) using Z Transform of x(h)]]
	+ [[#2-5 Find the Z Transform of exponential decay sine signals]]
	+ [[#2-6 Obtain the Z Transform of exponential signal multiple by time]]
	+ [[#2-7 Determine the initial value of a signal x(t) through its Z Transform]]
	+ [[#2-8 Determine the final value of a signal x(t) through its Z Transform]]
+ [[#Invert Z Transform]]
	+ [[#2-10 Find x(k) for k = 0, 1, 2, 3, 4 using Long Division]]
	+ [[#2-11 Obtain the inverse Z transform of a finite series X(z)]]
	+ [[#2-13 Use Difference Equation Approach for inverse Z transform]]
	+ [[#2-14 Using PFE for inverse Z transform - Simple Poles]]
	+ [[#2-15 Using PFE for inverse Z transform - Complex Conjugate Poles]]
	+ [[#2-16 Using Inversion Integral Method]]
	+ [[#2-17 Solve the difference equation using Z transform]]


---
## Proof of Z Transform Properties

#### Shifting Theorem - Delay

#### Shifting Theorem - Advance 




---
## Z Transform Calculation 

#### 2-1  Z Transform of Laplace Form Signal 

$$X(s)=\frac{1}{s(s+1)}$$
Firstly, compute the original continuous signal $x(t)$ from $X(s)$
$$X(s)=\frac{1}{s(s+1)}=\frac{1}{s}-\frac{1}{s+1}$$
Look up the Laplace Transform Table
$$x(t)=L^{-1}\{X(s)\}=1-e^{-t}$$
Properties used here: 
 + Linearity 
 + Multiplication by a exponential of $k$
$$\begin{align}
Z\{x(t)\}&=Z\{1\}-Z\{e^{-t}\}\\
&=\sum^{\infty}_{k=0}z^{-k}- \sum^{\infty}_{k=0}e^{-kT}z^{-k}\\
&=\frac{z}{z-1}-\sum^{\infty}_{k=0}(e^{T}z)^{-k}\\
&=\frac{z}{z-1}-\frac{e^Tz}{e^Tz-1}\\
&=\frac{z(1-e^{-T})}{(z-1)(z-e^{-T})}
\end{align}$$


#### 2-2  Find the Z Transform of a delayed unit step

$$1(t-4T)$$
The solution to this question is similar to the proof of Delay Shifting Theorem, you can use the theorem directly to get a one step solution.
$$\begin{align}
Z\{x(t)\}&=Z\{1(t-4T)\}\\
&=\sum_{k=0}^{\infty}1(kT-4T)z^{-k}\\
&=\sum_{k=4}^{\infty}z^{-k}\\
&=\frac{z^{-3}}{z-1}\\
&=z^{-4}\frac{z}{z-1}
\end{align}$$

#### 2-3  Obtain the Z Transform of a delayed exponential series

$$
f(k) =
\begin{cases}
    a^{k-1} &k=1,2,3,... \\
    0  & k\leq0
\end{cases}
$$
This function is the one step delayed version of $a^{k}$. With this discovery, the solution is obtained using two properties:
+ Delay Shifting Theorem
+ Multiplication by a exponential of $k$
$$\begin{align}
Z\{f(k)\}&=z^{-1}Z\{a^k\} \\
&= z^{-1} \sum_{k=0}^{\infty}a^kz^{-k}\\
&= z^{-1}1(a^{-1}z)\\
&= z^{-1} \frac{a^{-1}z}{a^{-1}z-1}\\
&= \frac{1}{z-a}
\end{align}$$

#### 2-4  Represent the Z Transform of y(k) using Z Transform of x(h)

$$\begin{cases}
x(h) &h=0,1,2,...\\
y(k)= \sum^{k}_{h=0}x(h) &k=0,1,2,...\\
\end{cases}$$
$y(k)=0$ for $k<0$

Directly using the definition is not possible for the complication of the expanding equation
$$Z\{y(k)\}=\sum^{\infty}_{k=0}[\sum^{k}_{h=0}x(h)]z^{-k}$$
Instead, you can spot some patterns from the equation of $y(k)$
$$\begin{align}y(0)&=x(0)\\
y(1)&=x(0)+x(1)\\
y(2)&=x(0)+x(1)+x(2)\\
&...
\end{align}$$
Seperate every value of $y(k)$ into two components
$$y(k)=y(k-1)+x(k)$$
Operate Z Transform on this whole equation and you will get the answer
$$\begin{align}Y(z)&=z^{-1}Y(z)+X(z)\\
Y(z)&=\frac{z}{z-1}X(z)\end{align}$$

#### 2-5  Find the Z Transform of exponential decay sine signals

$$\begin{align}x(t)&=e^{-at}\sin\omega t\\y(t)&=e^{-at} \cos \omega t\end{align}$$
The **Complex Translation Theorem** can be used here. Take $x(t)$ for example, the form of its Z Transform become similar to a sine signal's Z Transform after using the theorem
$$\begin{align}
Z\{x(t)\}&=\sum_{k=0}^{\infty}\sin(\omega kT) e^{-akT} z^{-k}\\
&= Z\{\sin(\omega t)\}|_{z=ze^{aT}}
\end{align}$$
Now calculate the Z Transform of sine signal, **Euler's Formula** is used here
$$\begin{align}
Z\{\sin(\omega t)\}&=
Z\{\frac{j(e^{-j\omega t}-e^{j\omega t})}{2}\}\\
&=\frac{j}{2} (Z\{e^{-j\omega t}\} - Z\{e^{j \omega t}\})\\
&=\frac{j}{2} (\sum_{k=0}^{\infty} e^{-j\omega kT}z^{-k}-\sum_{k=0}^{\infty}e^{j\omega kT}z^{-k})\\
&=\frac{j}{2} (\frac{ze^{j\omega T}}{ze^{j\omega T}-1} - \frac{ze^{-j\omega T}}{ze^{-j\omega T}-1})\\
&=\frac{z\sin{\omega T}}{z^2-2z\cos(\omega T)+1}

\end{align}$$
Finally you can calculate the Z Transform of $x(t)$
$$Z\{x(t)\}=Z\{\sin{\omega t}\} |_{z=ze^{aT}}=\frac{ze^{aT}\sin\omega T}{z^2 e^{2aT}-2ze^{aT}\cos(\omega T)+1}$$
Then, use the same method on $y(t)$
$$\begin{align}
Z\{y(t)\}&=\sum^\infty_{k=0}\cos(\omega kT)e^{-akT}z^{-k}\\
&=Z\{cos(\omega t)\}|_{z=ze^{aT}}\\
&=\frac{z^2e^{2aT}-ze^{aT}\cos(\omega T)}{z^2e^{2aT}-2ze^{aT}\cos(\omega T)+1}
\end{align}$$

#### 2-6  Obtain the Z Transform of exponential signal multiple by time

$$x(t)=te^{-at}$$
Firstly, use the **Complex Translation Theorem** to simplify the Z Transform equation
$$Z\{x(t)\}=Z\{t\}|_{z=ze^{aT}}$$The Z Transform of $t$ is not easy to compute, but actually it can be done by a similar approach to the Z Transform of unit step.
$$\begin{align}
Z\{t\}&=T\sum_{k=0}^{\infty}kz^{-k}\\
&=T\frac{(z-1)^2}{(z-1)^2}\sum_{k=0}^{\infty}kz^{-k}\\
&=T\frac{(z^2-2z+1)(0+1\cdot z^{-1}+2\cdot z^{-2}+3\cdot z^{-3}+...)}{(z-1)^2}\\
&=T\frac{z-2+z^{-1}+2-4z^{-1}+2z^{-2}+3z^{-1}-6z^{-2}+3z^{-3}+4z^{-2}-8z^{-3}+4z^{-4}+...}{(z-1)^2}\\
&=T\frac{z}{(z-1)^2}
\end{align}$$
Finally we get the Z Transform of $x(t)$
$$Z\{x(t)\}=Z\{t\}|_{z=ze^{aT}}=T\frac{ze^{aT}}{z^2 e^{2aT}-ze^{aT}+1}$$

#### 2-7  Determine the initial value of a signal x(t) through its Z Transform

$$X(z)=\frac{(1-e^{-T})z^{-1}}{(1-z^{-1})(1-e^{-T}z^{-1})}$$
Obviously the solution must use the **Initial Value Theorem**. Remember, this theorem only works when the limit in the formula exists.
$$\begin{align}
x(0)&=\lim_{z\to\infty}X(z)\\
&=\frac{(1-e^{-T})\cdot 0}{1 \cdot 1}\\
&=0
\end{align}$$

#### 2-8   Determine the final value of a signal x(t) through its Z Transform

$$X(z)=\frac{1}{1-z^{-1}}-\frac{1}{1-e^{-aT}z^{-1}} , a>0$$
Before using the **Final Value Theorem**, you must inspect all the poles of $X(z)$
$$\begin{align}
X(z)&=\frac{1}{1-z^{-1}}-\frac{1}{1-e^{-aT}z^{-1}}\\
&=\frac{-z^2+2z-e^{-aT}}{(z-1)(z-e^{-aT})}\\
\end{align}$$
Seems that $X(z)$ has two poles $z=1$ and $z=e^{-aT}$. With the condition $a>0$, both poles are inside the unit circle. Then everything is fine for the remain steps.
$$\begin{align}
\lim_{t\to\infty}x(t)&=\lim_{z\to1}(1-z^{-1})X(z)\\
&=\lim_{z\to1}\frac{-z^2+2z-e^{-aT}}{z(z-e^{-aT})}\\
&=1
\end{align}$$
Notice that you can calculate a result even when the pole condition isn't fulfilled, but the result is incorrect as the actual signal will apparently diverge.

---
## Invert Z Transform

#### 2-10  Find x(k) for k = 0, 1, 2, 3, 4 using Long Division

$$X(z)=\frac{10z+5}{(z-1)(z-0.2)}$$

Firstly, we rewrite both the numerator and denominator of the fraction-form Z transform in terms of $z^{-1}$ . In this way, we can directly get the sequence starts at $z$ to the power of $-1$
$$X(z)=\frac{10z^{-2}+5{z^{-3}}}{z^{-1}-1.2z^{-2}+0.2z^{-3}}$$
Remember, you should put the terms with larger power at the front of the polynomial when using the Polynomial Long Division. The method is very similar to the classical long division with numbers

![[4cb1f2d3f0a17a3a9ef580aa52101a8.jpg]]

Now we know that the first five number of sequence $x(k)$ is:

| k    | 0   | 1   | 2   | 3    | 4     | ... |
| ---- | --- | --- | --- | ---- | ----- | --- |
| x(k) | 0   | 10  | 17  | 18.4 | 18.68 | ... |

#### 2-11  Obtain the inverse Z transform of a finite series X(z)

$$X(z)=1+2z^{-1}+3z^{-2}+4z^{-3}$$
This answer is quiet simple. Since the $X(z)$ series is finite, the original signal is also finite in time.
$$x(k)=\begin{cases}k+1 & k=0,1,2,3\\0 & k>4\end{cases}$$


#### 2-13  Use Difference Equation Approach for inverse Z transform

$$H(z)=\frac{0.4673z-0.3393}{z^2-1.5327z+0.6607}$$
First we rewrite the transfer function in term of $z^{-1}$
$$H(z)=\frac{0.4673z^{-2}-0.3393z^{-3}}{z^{-1}-1.5327z^{-2}+0.6607z^{-3}}$$
Then obtain the differential equation from the transfer function.
$$0.4673x(k-2)-0.3393x(k-3)=y(k-1)-1.5327y(k-2)+0.6607y(k-3)$$
The final stage is to calculate the output sequence step by step with unit sample input
$$\begin{align} y(0)&=0\\y(1)&=0.4673\\y(2)&=\\y(3)&=\\... \end{align}$$

#### 2-14  Using PFE for inverse Z transform - Simple Poles

$$X(z)=\frac{(1-e^{-aT})z}{(z-1)(z-e^{-aT})}$$
The poles have been revealed. They are $z=1$ and $z=e^{-aT}$ , which are both simple poles. Then, only simple decomposition is required.

Notice that the Z transform expression contains a single $z$ in the numerator which represents **time shifting**. We move the $z$ to the left-hand side for simplicity.
$$\frac{X(z)}{z}=\frac{A}{z-1}+\frac{B}{z-e^{-aT}}$$
For unknown values $A,B$, obviously
$$A(z-e^{-aT})+B(z-1)=1-e^{-aT}$$
$$\begin{cases} A+B=0 \\ -Ae^{-aT} -B=1-e^{-aT} \end{cases}$$
Now we get the decomposed Z transform. The single $z$'s now cancelled out.
$$\begin{align}\frac{X(z)}{z}&=\frac{1}{z-1}-\frac{1}{z-e^{-aT}}\\
&=z^{-1}(\frac{1}{1-z^{-1}}-\frac{1}{1-e^{-aT}z^{-1}})\\X(z)&=\frac{1}{1-z^{-1}}-\frac{1}{1-e^{-aT}z^{-1}}\end{align}$$
Look up the Z Transform table and find the two useful transforms.
$$Z\{1(t)\}=\frac{1}{1-z^{-1}}$$
$$Z\{e^{-at}\}=\frac{1}{1-e^{-aT}z^{-1}}$$
Finally we get the original continuous signal
$$x(t)=1-e^{-at}$$


#### 2-15  Using PFE for inverse Z transform - Complex Conjugate Poles 

$$X(z)=\frac{z^2+z+2}{(z-1)(z^2-z+1)}$$




#### 2-16  Using Inversion Integral Method

$$X(z)=\frac{(1-e^{-aT})z}{(z-1)(z-e^{-aT})}$$
Since $X(z)z^{k-1}$ only has two simple poles $z=1$, $z=e^{-aT}$, the calculation is just a simple substitution.
$$\begin{align}x(k)=K_1+K_2&=\lim_{z\to 1}(z-1)X(z)z^{k-1}+\lim_{z\to e^{-aT}}(z-e^{-aT})X(z)z^{k-1}\\&=1-e^{-akT}\end{align}$$

#### 2-17  Solve the difference equation using Z transform

$$x(k+2)+3x(k+1)+2x(k)=0$$
$$x(0)=0 \quad x(1)=1$$
To solve the equation, we need to do the Z transform on it first, then try to find the closed-form expression using inverse Z transform.

To operate Z transform on the given differential equation, you need to use the advanced shifting theorem:
$$Z\{x(t+nT)\}=z^n[X(z)-\sum^{n-1}_{k=0}x(kT)z^{-k}]$$
The advanced terms can be written as
$$\begin{align}Z\{x(k+2)\}&=z^2[X(z)-x(0)-x(1)z^{-1}]=z^2X(z)-z\\Z\{x(k+1)\}&=z[X(z)-x(0)]=zX(z)\end{align}$$
Then do the Z transform
$$\begin{align}z^2X(z)-z+3zX(z)+2X(z)&=0\\X(z)&=\frac{z}{z^2+3z+2}\end{align}$$
Now we do the inverse transform, PFE method will grant us a closed-form result
$$X(z)=\frac{z}{z^2+3z+2}=z(\frac{1}{z+1}-\frac{1}{z+2})=\frac{1}{1+z^{-1}}-{\frac{1}{1+2z^{-1}}}$$
Check the Z transform table for the corresponding transform
$$Z\{a^k \cos( k\pi)\}=\frac{1}{1+az^{-1}}$$
The final result is the analytic (closed-form) expression of the given equation
$$\begin{align}x(k)&=(1-2^k)\cos( k\pi)\\&=(-1)^k-(-2)^k\end{align}$$
