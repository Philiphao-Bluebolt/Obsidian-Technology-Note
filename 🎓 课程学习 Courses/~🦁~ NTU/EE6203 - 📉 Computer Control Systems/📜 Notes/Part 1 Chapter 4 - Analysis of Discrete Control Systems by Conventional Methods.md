+ **Goal** - "Learn to analyze, then you will know how to design"

+ [[#Mapping from s plane to z plane]]
+ [[#Closed-loop Stability Analysis]]
	+ [[#Jury Criterion]]
	+ [[#Routh Criterion]]
+ [[#]]

---
## Mapping from s plane to z plane

+ **Goal** - Establish the relation between $s$ and $z$ domain

The impulse sampler equations have proven that discrete $z$ domain and continuous $s$ domain can be related by the following equation
$$z=e^{sT}=e^{(\sigma+j\omega)T}=e^{\sigma T}e^{j\omega T}$$
The magnitude and angle of the $z$ value is given as
$$\begin{cases}|z|=e^{\sigma T}\\\angle z=\omega T \end{cases}$$
+ $\sigma$ - the real part of $s$
+ $\omega$ - the imaginary part of $s$
+ $T$ - the sampling period

### 



### Stability Circle

The stability condition of a closed-loop continuous system is that all of its poles (eigenvalues) should be at the left-half of the s plane.



###



---
## Closed-loop Stability Analysis

+ **Goal** - Test if a closed-loop (complete) system is stable

Stability is the No.1 important performance of a system as unstable systems are useless for control. Although the pole condition for stability always works, sometimes it's too complicated compute all the poles from the characteristic polynomial especially when unknown coefficients exist.

### Jury Criterion 

Jury criterion is the discrete counterpart of continuous system's routh criterion. It's invented to directly test the stability of a discrete system from its characteristic polynomial.

The highest indexed coefficient in the characteristic polynomial is the constant and the lowest indexed is the coefficient of the highest power.
$$P(z)=a_0 z^{n}+a_1z^{n-1}+\dots+a_n$$
+ First row - coefficients of $P(z)$ in **ascending order of power**
+ Even rows - reverse of the previous row
+ Odd rows - the determinant whose elements are from the first column and the upper-right column of the previous two rows.
$$b_{n-1}=\begin{vmatrix}\color{red}a_n&\color{blue}a_{n-1}\\\color{red}a_0&\color{blue}a_1\end{vmatrix} \quad b_{n-2}=\begin{vmatrix}\color{red}a_n&\color{brown}a_{n-2}\\\color{red}a_0&\color{brown}a_2\end{vmatrix} \quad \dots$$
+ Every odd row is one element shorter than the previous odd row
+ Final row - the last row of the table is the $2n-3$ row which has 3 elements 

|   Rows   |         $z^0$         |         $z^1$          |         $z^2$          |   $z^3$   | $\dots$  |       $z^{n-2}$        |       $z^{n-1}$       | $z^{n}$ |
| :------: | :-------------------: | :--------------------: | :--------------------: | :-------: | :------: | :--------------------: | :-------------------: | :-----: |
|   $1$    |   $\color{red}a_n$    | $\color{blue}a_{n-1}$  | $\color{brown}a_{n-2}$ | $a_{n-3}$ | $\dots$  |         $a_2$          |         $a_1$         |  $a_0$  |
|   $2$    |   $\color{red}a_0$    |   $\color{blue}a_1$    |   $\color{brown}a_2$   |   $a_3$   | $\dots$  |       $a_{n-2}$        |       $a_{n-1}$       | $a_{n}$ |
|   $3$    | $\color{blue}b_{n-1}$ | $\color{brown}b_{n-2}$ |       $b_{n-3}$        | $b_{n-4}$ | $\dots$  |         $b_1$          |         $b_0$         |         |
|   $4$    |         $b_0$         |         $b_1$          |         $b_2$          |   $b_3$   | $\dots$  | $\color{brown}b_{n-2}$ | $\color{blue}b_{n-1}$ |         |
|   $5$    |       $c_{n-2}$       |       $c_{n-3}$        |       $c_{n-4}$        | $c_{n-5}$ | $\dots$  |        $c_{0}$         |                       |         |
|   $6$    |        $c_{0}$        |        $c_{1}$         |        $c_{2}$         |  $c_{3}$  | $\dots$  |       $c_{n-2}$        |                       |         |
| $\vdots$ |       $\vdots$        |        $\vdots$        |        $\vdots$        | $\vdots$  | $\vdots$ |                        |                       |         |
|  $2n-3$  |         $q_2$         |         $q_1$          |         $q_0$          |           |          |                        |                       |         |

The system is stable if the Jury table fulfills all the following conditions

1. $z=1$ condition
$$P(z)|_{z=1}>0$$
2. $z=-1$ condition
$$P(z)|_{z=-1}\begin{cases}>0& \mathrm{even}\quad n\\<0& \mathrm{odd}\quad n\end{cases}$$
3. Characteristic polynomial condition
$$|a_n|<a_0$$
4. First element condition
$$\begin{cases}|b_{n-1}|>|b_0|\\|c_{n-2}|>|c_0|\\\dots\\|q_2|>|q_0|\end{cases}$$

### Routh Criterion





---
## 