
+ [Question 1](#Question%201)
	+ [(1) Coprimeness of two matrices](#(1)%20Coprimeness%20of%20two%20matrices)
	+ [(2) Row Hermite Form Transform and Common Right Divisor](#(2)%20Row%20Hermite%20Form%20Transform%20and%20Common%20Right%20Divisor)
	+ [(3) Column Reduction](#(3)%20Column%20Reduction)
+ [Question 2](#Question%202)
	+ [(1) Coprime Right Polynomial Fraction Description](#(1)%20Coprime%20Right%20Polynomial%20Fraction%20Description)
	+ [(2)(3) Poles, Transmission Zeros, and Column Reduction](#(2)(3)%20Poles,%20Transmission%20Zeros,%20and%20Column%20Reduction)
	+ [(4) Minimal Realization](#(4)%20Minimal%20Realization)
+ [Question 3](#Question%203)
	+ [CRPFD Calculation](#CRPFD%20Calculation)
	+ [Integrator Coefficient Matrices](#Integrator%20Coefficient%20Matrices)
	+ [Lyapunov Equation](#Lyapunov%20Equation)
+ [Question 4](#Question%204)


---
## Question 1


### (1) Coprimeness of two matrices

To determine the coprimeness of two matrices, the rank of their augmented matrix is calculated.
$$\begin{align}M(s)=\begin{bmatrix}D(s)\\N(s)\end{bmatrix}&=\begin{bmatrix}(s+2)^2 & s+2\\s+2 & s^3+8\\s+2 & (s+2)^2\\(s+2)(s+3)&(s+4)(s^2-4)\end{bmatrix}\end{align}$$
Since the elements from the first column share the term $s+2$, the rank of the matrix decays to 1 when $s=-2$, meaning $D(s)$ and $N(s)$ are not coprime.

### (2) Row Hermite Form Transform and Common Right Divisor

The unimodular transform matrix $U(s)$ can be obtained by attaching a identity matrix to $M(s)$ and do the elementary row operation on both sides simultaneously.

$$\begin{align}[M(s)|I_{4\times4}]&=\begin{bmatrix}(s+2)^2 & s+2&1&0&0&0\\s+2 & s^3+8 &0&1&0&0\\s+2 & (s+2)^2&0&0&1&0\\(s+2)(s+3)&(s+4)(s^2-4)&0&0&0&1\end{bmatrix}\\&\to \begin{bmatrix}0&(s+2)-(s+2)^3&1 & 0 & -(s+2)&0\\0&s^3+8-(s+2)^2&0&1&-1&0\\s+2&(s+2)^2&0&0&1&0\\0&(s+4)(s^2-4)-(s+2)^2(s+3)&0&0&-(s+3)&1\end{bmatrix}\\&\to\begin{bmatrix}0 & -s^2-3s-1&1&0&-(s+2)&0\\0&7s+8&-4&1&4s-7&0\\s+2&\frac{5}{3}&0&0&-\frac{4}{9}s-\frac{1}{3}&\frac{4}{9}\\0&-\frac{9}{4}s-3&0&0&-s-3&1\end{bmatrix}\\&\to\begin{bmatrix}s+2&0&\frac{5}{4}s-\frac{75}{9}&\frac{5}{4}&-\frac{5}{4}s^2+\frac{3}{2}s+\frac{41}{12}&\frac{31}{9}\\0&1&-\frac{3}{4}s+\frac{16}{3}&-\frac{3}{4}&\frac{3}{4}s^2-\frac{3}{2}s-\frac{35}{12}&-\frac{7}{3}\\0&0&-\frac{35}{28}s^2+\frac{103}{12}s+\frac{19}{3}&-\frac{5}{4}s-\frac{3}{4}&\frac{5}{4}s^3-\frac{7}{4}s^2-\frac{83}{12}s&-\frac{59}{12}\\0&0&\frac{21}{4}s^2-21s-\frac{140}{3}&\frac{21}{4}s+7&-\frac{21}{4}s^3+\frac{7}{2}s^2+\frac{413}{12}s+\frac{91}{3}&\frac{49}{3}s+\frac{56}{3}\end{bmatrix}\end{align}$$

The detailed operations: ($r_i$ means the $i$-th row)

+ $r_1\leftarrow r_1-(s+2)r_3$
+ $r_2 \leftarrow r_2 - r_3$
+ $r_4 \leftarrow r_4-(s+3)r_3$
+ $r_2 \leftarrow r_2 +sr_1$
+ $r_3\leftarrow r_3+r_1$
+ $r_4 \leftarrow r_4 - r_1$
+ $r_2\leftarrow r_2-4r_1$
+ $r_3\leftarrow r_3+\frac{4}{9}r_4$
+ $r_1\leftarrow r_1+\frac{1}{7}sr_2$
+ $r_4 \leftarrow r_4 +\frac{9}{28}r_2$
+ $r_4\leftarrow -\frac{7}{3}r_4$
+ $r_1\leftarrow r_1 -(-\frac{13}{7}s-1)r_4$
+ $r_2\leftarrow r_2 -(7s+8)r_4$
+ $r_1\leftrightarrow r_3$
+ $r_2\leftrightarrow r_4$
+ $r_1 \leftarrow r_1 -\frac{5}{3} r_2$

The unimodular matrix $U(s)$ and common right divisor $R(s)$

$$U(s)=\begin{bmatrix}\frac{5}{4}s-\frac{75}{9}&\frac{5}{4}&-\frac{5}{4}s^2+\frac{3}{2}s+\frac{41}{12}&\frac{31}{9}\\-\frac{3}{4}s+\frac{16}{3}&-\frac{3}{4}&\frac{3}{4}s^2-\frac{3}{2}s-\frac{35}{12}&-\frac{7}{3}\\-\frac{35}{28}s^2+\frac{103}{12}s+\frac{19}{3}&-\frac{5}{4}s-\frac{3}{4}&\frac{5}{4}s^3-\frac{7}{4}s^2-\frac{83}{12}s&-\frac{59}{12}\\\frac{21}{4}s^2-21s-\frac{140}{3}&\frac{21}{4}s+7&-\frac{21}{4}s^3+\frac{7}{2}s^2+\frac{413}{12}s+\frac{91}{3}&\frac{49}{3}s+\frac{56}{3}\end{bmatrix}$$
$$R(s)=\begin{bmatrix}s+2&0\\0&1\end{bmatrix}$$
### (3) Column Reduction

The coprime description matrices 

$\hat{N}(s)=N(s)R^{-1}(s)=\begin{bmatrix}s+2 & (s+2)^2\\(s+2)(s+3)&(s+4)(s^2-4)\end{bmatrix}\begin{bmatrix}\frac{1}{s+2}&0\\0&1\end{bmatrix}=\begin{bmatrix}1&(s+2)^2\\s+3&(s+4)(s^2-4)\end{bmatrix}$
$$\hat{D}(s)=D(s)R^{-1}(s)=\begin{bmatrix}(s+2)^2 & s+2\\s+2 & s^3+8\end{bmatrix}\begin{bmatrix}\frac{1}{s+2}&0\\0&1\end{bmatrix}=\begin{bmatrix}s+2&s+2\\1&s^3+8\end{bmatrix}$$
Since $\deg\det\hat{D}=4=c_1(\hat{D})+c_2(\hat{D})=3+1$, $D(s)$ is column reduced.

---
## Question 2


### (1) Coprime Right Polynomial Fraction Description

Since the divisor in the first column of matrix $G(s)$ have the least common multiple $(s+1)^2(s+4)$
and it's $(s+4)^2(s+1)$ for the second column, one set of the $D(s)$ and $N(s)$ is obtained.

$$G(s)=N(s)D^{-1}(s)=\begin{bmatrix}2(s+1)(s+4) & 2(s+1)(s+4)\\(s+2)(s+4)&(s+2)(s+4)\\(s+2)(s+1)&(s+2)(s+1)\end{bmatrix}\begin{bmatrix}(s+1)^2(s+4)&0\\0&(s+4)^2(s+1)\end{bmatrix}^{-1}$$
Calculate the greatest common right divisor of $N(s)$ and $D(s)$. The result shows that the two matrices are not coprime since the rank of the augmented matrix degenarates to 1 when $s=-1$ or $s=-4$

$$\begin{align}\begin{bmatrix}D(s)\\N(s)\end{bmatrix}&=\begin{bmatrix}(s+1)^2(s+4)&0\\0&(s+4)^2(s+1)\\2(s+1)(s+4) & 2(s+1)(s+4)\\(s+2)(s+4)&(s+2)(s+4)\\(s+2)(s+1)&(s+2)(s+1)\end{bmatrix}\to\begin{bmatrix}(s+1)^2(s+4)&0\\0&(s+4)^2(s+1)\\4(s+1)&4(s+1)\\3(s+2)&3(s+2)\\(s+2)(s+1)&(s+2)(s+1)\end{bmatrix}\\&\to\begin{bmatrix}(s+1)^2(s+4)&0\\0&(s+4)^2(s+1)\\4(s+1)&4(s+1)\\1&1\\(s+2)(s+1)&(s+2)(s+1)\end{bmatrix}\to\begin{bmatrix}0&-(s+1)^2(s+4)\\0&(s+4)^2(s+1)\\0&0\\1&1\\0&0\end{bmatrix}\to \begin{bmatrix}1&1\\0&4(s+1)(s+4)\\0&0\\0&0\\0&0\end{bmatrix}\end{align}$$

The detailed row operations are listed below

+ $r_3\leftarrow r_3 - 2r_5$
+ $r_4\leftarrow r_4-r_5$
+ $r_4 \leftarrow \frac{1}{3}(r_4-\frac{3}{4}r_3)$
+ $r_1 \leftarrow r_1 - (s+1)^2(s+4)r_2$
+ $r_3 \leftarrow r_3 - 4(s+1)r_4$
+ $r_5 \leftarrow r_5-(s+1)(s+2)r_4$
+ $r_1\leftarrow r_1 + r_2$
+ $r_2 \leftarrow r_2 -\frac{1}{3}s r_1$
+ $r_1\leftarrow r_1 -\frac{3}{4}r_2$
+ $r_1 \leftrightarrow r_4$

The greatest common right divisor $R(s)$
$$R(s)=\begin{bmatrix}1&1\\0&4(s+1)(s+4)\end{bmatrix}$$
$$R^{-1}(s)=\begin{bmatrix}1&-\frac{1}{4(s+1)(s+4)}\\0&\frac{1}{4(s+1)(s+4)}\end{bmatrix}$$
Transform $D(s)$ and $N(s)$ to a coprime pair
$$\hat{D}(s) =D(s)R^{-1}(s)=\begin{bmatrix}-(s+1)^2(s+4)&\frac{s+1}{4}\\0&\frac{s+4}{4}\end{bmatrix}$$
$$\hat{N}(s)=N(s)R^{-1}(s)=\begin{bmatrix}2(s+1)(s+4)&0\\(s+2)(s+4)&0\\(s+2)(s+1)&0\end{bmatrix}$$
### (2)(3) Poles, Transmission Zeros, and Column Reduction

The degree of $\det{\hat{D}}(s)$ is equal to the sum of greatest degree from every columms, so the matrix $D(s)$ is column reduced
$$\deg[\det\hat{D}(s)]=4=c_1[\hat{D}]+c_2[\hat{D}]=3+1$$
Since the description is column reduced, the poles and transmission zeros can be obtained through the following definition

+ Poles make $D(s)$ singular
$$\begin{align}\det{\hat{D}(s)}&=-\frac{1}{4}(s+1)^2(s+4)=0\\s&=-1,-4\end{align}$$
+ Zeros reduce the rank of $N(s)$, which is already a sigular matrix with rank of 1
$$\mathrm{rank}[{\hat{N}(s)}] < \mathrm{rank}[\hat{N}]=1\quad\leftrightarrow\quad \begin{cases}2(s+1)(s+4)=0\\(s+2)(s+4)=0\\(s+2)(s+1)=0\end{cases} \quad\to\quad \emptyset$$
As a result, the original system $G(s)$ has two poles $-1$ and $-4$ but no transmission zero.

### (4) Minimal Realization

Since $\hat{D}(s)$ and $\hat{N}(s)$ are column reduced CRPFD of $G(s)$ 
$$\alpha_1=c_1[\hat{D}]=3\quad\alpha_2=c_2[\hat{D}]=1$$
Integrator Coefficient Matrices
$$A_o=\begin{bmatrix}0 &1&0&\\0&0&1&\\0&0&0&\\&&&0\end{bmatrix}\quad B_o=\begin{bmatrix}0&\\0&\\1&\\&1\end{bmatrix} \quad \Psi=\begin{bmatrix}1&\\s&\\s^2&\\&1\end{bmatrix}\quad \Delta=\begin{bmatrix}s^3&\\&s\end{bmatrix}$$
Factorization of $N(s)$ and $D(s)$
$$N_l=\begin{bmatrix}8&10&2&0\\8&6&1&0\\2&3&1&0\end{bmatrix}\quad D_{hc}= \begin{bmatrix}-1&\frac{1}{4}\\0&\frac{1}{4}\end{bmatrix}\quad D_l=\begin{bmatrix}-4&-9&-6&\frac{1}{4}\\0&0&0&1\end{bmatrix}$$
The state space matrices
$$A=A_o -B_oD_{hc}^{-1}D_l=\begin{bmatrix}0&1&0&0\\0&0&1&0\\-4&-9&-6&-\frac{3}{4}\\0&0&0&-4\end{bmatrix}$$
$$B=B_oD_{hc}^{-1}=\begin{bmatrix}0&0\\0&0\\-1&1\\0&4\end{bmatrix}$$
$$C=N_l=\begin{bmatrix}8&10&2&0\\8&6&1&0\\2&3&1&0\end{bmatrix}$$
---
## Question 3

The process of feedback control design 

1. Calculating CRPFD $D(s)$ and $N(s)$
2. Computing the integrator coefficient matrices
3. Pole Placement 

### CRPFD Calculation

Construct a diagonal $D(s)$ matrix with its diagonal elements equal to the column least common multiples of $G(s)$

$$G(s)=N(s)D^{-1}(s)=\begin{bmatrix}2(s+1)&2(s+1)(s+4)\\s+2&(s+2)
(s+4)\end{bmatrix}\begin{bmatrix}(s+1)^2&\\&(s+4)^2(s+1)\end{bmatrix}^{-1}$$

Obtain the greatest common right divisor of $D(s)$ and $N(s)$ as well as checking the coprimeness. The result shows that the two matrices are not coprime.

$$\begin{align}\begin{bmatrix}D(s)\\N(s)\end{bmatrix}&=\begin{bmatrix}(s+1)^2&\\&(s+4)^2(s+1)\\2(s+1)&2(s+1)(s+4)\\s+2&(s+2)(s+4)\end{bmatrix}\to \begin{bmatrix}(s+1)^2&\\&(s+4)^2(s+1)\\1&s+4\\s+2&(s+2)(s+4)\end{bmatrix}\\&\to\begin{bmatrix}0&-(s+4)(s+1)^2\\0&(s+4)^2(s+1)\\1&s+4\\0&0\end{bmatrix}\to\begin{bmatrix}0&3s^2+15s+12\\0&s^3+9s^2+24s+16\\1&s+4\\0&0\end{bmatrix}\to\begin{bmatrix}1&s+4\\0&4s^2+20s+16\\0&0\\0&0\end{bmatrix}\end{align}$$

Detailed row transform

+ $r_3\leftarrow -\frac{1}{2}(r_3-2r_4)$
+ $r_1\leftarrow r_1 -(s+1)^2r_3$
+ $r_4\leftarrow r_4-(s+2)r_3$
+ $r_1 \leftarrow r_1+r_2$
+ $r_2 \leftarrow r_2 - \frac{s}{3}r_1$
+ $r_1\leftarrow r_1-\frac{3}{4}r_2$
+ $r_1\leftrightarrow r_2$

The greatest common right divisor $R(s)$
$$R(s)=\begin{bmatrix}1&s+4\\0&4s^2+20s+16\end{bmatrix}\quad R^{-1}(s)=\begin{bmatrix}1 &-\frac{1}{4(s+1)}\\0&\frac{1}{4(s+1)(s+4)}\end{bmatrix}$$
The CRPFD matrices
$$\hat{N}(s)=N(s)R^{-1}(s)=\begin{bmatrix}2(s+1)&2(s+1)(s+4)\\s+2&(s+2)
(s+4)\end{bmatrix}\begin{bmatrix}1 &-\frac{1}{4(s+1)}\\0&\frac{1}{4(s+1)(s+4)}\end{bmatrix}=\begin{bmatrix}2(s+1)&0\\s+2&
0\end{bmatrix}$$
$$\hat{D}(s)=D(s)R^{-1}(s)=\begin{bmatrix}(s+1)^2&\\&(s+4)^2(s+1)\end{bmatrix}\begin{bmatrix}1 &-\frac{1}{4(s+1)}\\0&\frac{1}{4(s+1)(s+4)}\end{bmatrix}=\begin{bmatrix}(s+1)^2&-\frac{s+1}{4}\\&\frac{s+4}{4}\end{bmatrix}$$

Checking if $\hat{D}(s)$ is column reduced. The result shows that the matrix is already column reduced. 
$$\deg[\det\hat{D}(s)]=\deg[\frac{(s+4)(s+1)^2}{4}]=3=c_1(\hat{D}(s))+c_2(\hat{D}(s))=2+1$$

### Integrator Coefficient Matrices

Constructing the integrator coefficient matrices.
$$A_o=\begin{bmatrix}0&1&\\&0&\\&&0\end{bmatrix}\quad B_o=\begin{bmatrix}0&\\1&\\&1\end{bmatrix}\quad \Psi(s)=\begin{bmatrix}1&\\s&\\&1\end{bmatrix}\quad \Delta=\begin{bmatrix}s^2&\\&s\end{bmatrix}$$
Calculating the matrices $N_l, D_{hc},D_l$
$$N_l=\begin{bmatrix}2&2&0\\2&1&0\end{bmatrix}\quad D_{hc}=\begin{bmatrix}1&-\frac{1}{4}\\0&\frac{1}{4}\end{bmatrix}\quad D_l=\begin{bmatrix}1&2&-\frac{1}{4}\\0&0&1\end{bmatrix}$$
Calculating the state space matrices
$$A=A_o-B_oD_{hc}^{-1}D_l=\begin{bmatrix}0&1&\\&0&\\&&0\end{bmatrix}-\begin{bmatrix}0&\\1&\\&1\end{bmatrix}\begin{bmatrix}1&1\\&4\end{bmatrix}\begin{bmatrix}1&2&-\frac{1}{4}\\&&1\end{bmatrix}=\begin{bmatrix}&1&\\-1&-2&-\frac{3}{4}\\&&-4\end{bmatrix}$$
$$B=B_oD_{hc}^{-1}=\begin{bmatrix}0&0\\1&1\\0&4\end{bmatrix}$$
$$C=N_l=\begin{bmatrix}2&2&0\\2&1&0\end{bmatrix}$$
### Lyapunov Equation

Checking the eigenvalue of the original system
$$\begin{align}A-\lambda I&=(\lambda^2-2\lambda-1)(4-\lambda)\\&=1+\sqrt{2},1-\sqrt{2},4\end{align}$$
All desired poles are located at $s=3$. Choose the matrix $F$ in observable canonical form and $\bar{k}$ in augmented identity form. The pair $(F,\bar{k})$ is controllable.
$$F=\begin{bmatrix}-3&1&\\-3&&1\\-3&&\end{bmatrix}\quad\bar{k}=\begin{bmatrix}1&0&0\\0&1&0\end{bmatrix}$$
$$\begin{align}AT-TF&=B\bar{k}\\\begin{bmatrix}0&1&0\\-1&-2&-\frac{3}{4}\\0&0&-4\end{bmatrix}T-T\begin{bmatrix}-3&1&\\-3&&1\\-3&&\end{bmatrix}&=\begin{bmatrix}0&0\\1&1\\0&4\end{bmatrix}\begin{bmatrix}1&0&0\\0&1&0\end{bmatrix}\end{align}$$
$$T=\begin{bmatrix}-\frac{22}{50}&\frac{11}{50}&\frac{8}{25}\\\frac{51}{50}&-\frac{22}{25}&\frac{11}{50}\\-\frac{36}{25}&-\frac{16}{25}&\frac{4}{25}\end{bmatrix}$$
Calculating the feedback gain matrix
$$K=\bar{K}T^{-1}=\begin{bmatrix}0&\frac{1}{3}&-\frac{11}{24}\\\frac{2}{3}&-\frac{4}{9}&-\frac{13}{18}\end{bmatrix}$$

---
## Question 4

The augmented system includes an extra state $x_a$ from the output of the integration loop. 
$$\begin{bmatrix}\dot{x}\\\dot{x}_a\end{bmatrix}=\begin{bmatrix}A+Bk&Bk_a\\-C&0\end{bmatrix}\begin{bmatrix}x\\x_a\end{bmatrix}+\begin{bmatrix}1\\0\end{bmatrix}w+\begin{bmatrix}0\\1\end{bmatrix}r$$
The closed loop state transition matrix
$$A_c=\begin{bmatrix}k_1-2&k_2+3&k_a\\k_1+2&k_2+4&k_a\\-1&-1&0\end{bmatrix}$$

Set all poles at $s=-2$ for stability
$$\begin{align}|sI-A|&=s^3+(-k_1-k_2-2)s^2+(2k_a+k_1-4k_2-14)s+(-2k_ak_1-2k_ak_2-7k_a)\\&=s^3+6s^2+12s+8\end{align}$$
Final result
$$k=\begin{bmatrix}k_1&k_2\end{bmatrix}=\begin{bmatrix}-\frac{308}{45}&-\frac{52}{45}\end{bmatrix}\quad k_a=\frac{8}{9}$$

---

![](EE7204_2526S1_Assignment.pdf)