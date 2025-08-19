MIMO systems have more than one inputs and outputs. Each output of the system is not the result of a sole input but the combination response of all the inputs, leading to complicated coupling. This phenomenon is known as the **Off-Diagonal Interaction**

+ **MIMO Model**
	+ [Transfer Function Matrix](#Transfer%20Function%20Matrix)
		+ [Sensitivity Function](#Sensitivity%20Function)
	+ [State Space](#State%20Space)
		+ Controllability and Observability
		+ Matrix Fraction Description
	+ Rank
	+ Poles and Zeros
+ **Input-output Pairing**
	+ [Relative Gain Array (RGA)](#Relative%20Gain%20Array%20(RGA))
		+ [Properties](#Properties)
		+ [Meaning](#Meaning)
		+ [Steady State RGA](#Steady%20State%20RGA)
	+ [Input-output Pairing](#Input-output%20Pairing)
		+ [Open-loop Interaction](#Open-loop%20Interaction)
		+ [Closed-loop Interaction](#Closed-loop%20Interaction)
		+ [Controller Pairing](#Controller%20Pairing)
	+ [Niederlinski’s Theorem](#Niederlinski’s%20Theorem)
	+ [Ill-Condition Elimination](#Ill-Condition%20Elimination)
		+ [Singular Value Analysis](#Singular%20Value%20Analysis)
+ **Controller Design**
	+ [Decentralized Control](#Decentralized%20Control)
	+ [Decoupling](#Decoupling)
+ **Examples**
	+ [Example - Controller Pairing (RGA & NI)](#Example%20-%20Controller%20Pairing%20(RGA%20&%20NI))
	+ [Example - Decoupling for Plant with Delay](#Example%20-%20Decoupling%20for%20Plant%20with%20Delay)

---
## Transfer Function Matrix

In a MIMO system, **each output would be affected by every inputs**. As a result, using only one transfer function is not enough to completely describe the response model of a MIMO system. Instead, we have to use a matrix.

The following block diagram of a two inputs, two outputs MIMO system shows that output $Y_{1}$ is affected by $U_1$ through $G_{11}$ and $U_2$ through $G_{12}$

![](Pasted%20image%2020250430084339.png)

> **Transfer Function Matrix**
$$Y(s)=G(s)U(s)$$
$$\begin{bmatrix}y_1(s)\\y_2(s)\\\vdots\\y_m(s)\end{bmatrix}=\begin{bmatrix}G_{11}(s) & G_{12}(s) & \cdots &G_{1n}(s)\\G_{21}(s)&G_{22}(s)&\cdots&G_{2n}(s)\\\vdots&\vdots&\ddots&\vdots\\\\G_{m1}(s)&G_{m2}(s)&\cdots&G_{mn}(s)\end{bmatrix}\begin{bmatrix}u_1(s)\\u_2(s)\\\vdots\\u_n(s)\end{bmatrix}$$

+ Number of outputs $Y(s)$ (controlled variable) - $m$
+ Number of inputs $U(s)$ (manipulated variable) - $n$
+ Shape of Transfer Function Matrix $G(s)$  - $m\times n$

### Sensitivity Function

+ **Goal** - describing performance trade-off in the control system

Sensitivity Functions are defined to describe several 





---
## State Space

State Space is naturally suitable for a MIMO system since the matrix representation can hold multiple inputs and outputs.

### Controllability and Observability



### Matrix Fraction Description






### 




---
## Relative Gain Array (RGA)

+ **Function** - evaluate the interaction of each input-output pair

The Relative Gain Array of a square MIMO system $Y(s)=G(s)U(s)$ (same numbers of input and output) can be calculated by its transfer function matrix $G(s)$
$$\Lambda=G(s)\odot G^{-T}(s)$$
+ $\odot$ - the Hadamard (element-wise) multiplication
+ $G^{-T}(s)$ - the inverse transpose of $G(s)$

Each element $\lambda_{ij}$ in the RGA matrix $\Lambda$ represents the strength of interaction from input $u_j$ to output $y_i$. This element is actually the ratio of each pair's open-loop gain to closed-loop gain.

Here we only discuss RGA for **square system** to avoid the complexity of generalizing matrix inverse operation, but actually it can apply to non-square system as well.

### Properties

RGA has some beneficial properties

> 1. **Dimensionlessness** - all the elements in the matrix are dimensionless and thus have no physical units.
>
> 2. **Scaling Independence** - the RGA matrix remains unchanged even if any element transfer function $G_{ij}$ is scaled by a constant (probably caused by the unit change of $u_j$ or $y_i$) 
>
> 3. **Normalization** - the sum of all elements in any rows or columns always equal to 1
>
> 4. **Identity RGA for Triangular Matrix** - if the system transfer funtion matrix is triangular, the result RGA is always a identity matrix

### Meaning

Every transfer function element in the RGA matrix represents a 




### Steady State RGA

+ **What is it** - RGA matrix in steady state ($s=0$)

While regular RGA is a function of the complex frequency $s$ and thus can describe input-output pair interaction at any frequency, the steady state RGA focuses on the static circumstance in which $s=0$
$$\Lambda_{ss}(G)=\Lambda(G(0))=\Lambda(K)$$

---
## Input-output Pairing

+ **Goal** - pairing inputs and outputs to decide the feedback structure for controller design

When implementing the controller and feedback, The pairing of controlled variables $Y(s)$ and manipulated variables $U(s)$ is a significant considerations.

Here're two pairing configurations for a 2-input-2-output MIMO system. When an output $Y_i$ and an input $U_j$ is paired, the feedback loop of that output is connected to the manipulated input $U_j$ through a controller.  

> $U_1 \longleftrightarrow Y_1, U_2 \longleftrightarrow Y_2$

![](Pasted%20image%2020250430180715.png)
> $U_1 \longleftrightarrow Y_2, U_2 \longleftrightarrow Y_1$

![](Pasted%20image%2020250430180759.png)

### Open-loop Interaction

When there's no feedback loops in the MIMO control system, 




### Closed-loop Interaction




### Controller Pairing

+ **Goal** - choose the pairs of controller based on the RGA matrix
+ **Tips** - choose those approximate 1 and avoid negative ones. 

The controller pairing is based on the elements of the RGA matrix. The sign of a element implies its response sign and its distance to 1 indicates the independence from other closed-loop inputs. 

+ $\lambda_{ij}<0$ - (**Avoid**) the change of input $u_j$ causes **inverse** response on $y_i$
+ $\lambda_{ij}>0$
	+ $\lambda_{ij}<1$ - the closing of other input routine **reduces** the control effect of current input 
	+ $\lambda_{ij}\approx1$ - (**Best**) the pair is almost not affected by other closed-loop input 
	+ $\lambda_{ij}>1$ - the closing of other input routine **enhances** the control effect of current input 

Always choose $\lambda_{ij}\approx1$ if applicable

---
## Niederlinski’s Theorem

+ **Function** - check the possibility to achieve closed-loop stability for a specific controller pairing

Niederkinski's Theorem is a **sufficient condition** for closed-loop stability of a MIMO controller-pairing scheme. 

> **Niederlinski's Index (NI)**
$$\mathrm{NI}=\frac{|G(0)|}{\prod^n_{i=1}G_{ii}(0)}$$
+ $|G(0)|$ - determinant of transfer function matrix when $s=0$
+ $\prod^n_{i=1}G_{ii}(0)$ - the product of all diagonal elements when $s=0$ (The rows or columns of the transfer function $G(s)$ should be shifted to move all the elements of selected pairings to the **diagonal**)

> **Niederlinski’s Theorem** - There's no possible closed-loop stable controllers for the selected pair scheme if it has a **negative** Niederlinski's Index (NI).
$$\mathrm{NI}=\frac{|G(0)|}{\prod^n_{i=1}G_{ii}(0)}<0$$

Notice that a non-negative value doesn't imply the existence of closed-loop stable controller set. It only means that it **may** exist, providing hope but not guarantee.

---
## Ill-Condition Elimination

+ **Condition** - singular or nearly singular transfer function matrix
+ **Solution** - eliminate some inputs (columns) and outputs (rows) of the transfer function matrix

There exists an ill-condition when the transfer function matrix has no inverse in steady state because $K=G(0)$ is singular. This implys that the system has redundant inputs or outputs which is linear dependant on others.
$$|K|=0$$
Another situation is that the elements of the transfer function matrix approximate a singular matrix, making it hard to control as some outputs would become very **sensative** to some inputs, amplifying the **noise**.

### Singular Value Analysis

+ **Goal** - derive the condition number to check the control difficulty of a MIMO system
+ **See also** - [⚙ Singular Value Decomposition](⚙%20矩阵运算%20Matrix%20Operations.md#奇异值分解%20Singular%20Value%20Decomposition)

The singular value decomposition breaks a matrix into three multiplying matrices. As a square matrix, the steady state transfer function matrix can be decomposited into three square matrices. The middle diagonal matrix $\Sigma$ includes all the **singular values** of the system
$$K=U\Sigma V^T$$

> **Singular Values** $\{\sigma_1,\sigma_2,\dots,\sigma_n\}$ - the diagonal elements of SVG middle matrix $\Sigma$, they're the **positive** square root of the eigenvalues of $K^TK$ 

$$K=U\begin{bmatrix}\sigma_1& &\\& \sigma_2 &\\ & & \ddots\\ & & &\sigma_n\end{bmatrix} V^T$$

> **Condition Number (CN)** - the ratio of the largest singular value to the smallest one. Always larger than 1
$$\mathrm{CN}=\frac{\sigma_{\max}}{\sigma_{\min}}$$
+ $\mathrm{CN}=1$ - ideal condition 
+ $\mathrm{CN} > 10$ - **oversensative**
+ $\mathrm{CN} \to \infty$ - nearly singular

If the system has a $\mathrm{CN} > 10$, some outputs and inputs should be eliminated to prevent instability caused by high sensativity.

---
## Decentralized Control

+ **Goal** - individually design each controllers and neglect the coupling

Decentralized control design treats each control loop as a seperated system with no consideration on the coupled side routine.

> 1. **Biggest Log Modulus Tuning (BLT)** - 
> 2. **Sequential** - 
> 3. **Parallel** - 
> 4. **Independent Design** - 

---
## Decoupling

+ **Goal** - convert the MIMO systems into with several SISO systems with a decoupler

Decoupling a MIMO system is to diagonalize its transfer function matrix $G(s)$ by a serial decoupler module $W(s)$
$$G(s)W(s)=G_{des}(s)$$
The desired transfer function matrix $G_{des}(s)$ is usually set as a multiple of the identity matrix. It has to include the **longest time delay** and **RHP transmission zeros** of the system $G(s)$
$$G_{des}(s)=aI$$

---
## Example - Controller Pairing (RGA & NI)

> [!NOTE] Question
> Given the steady state transfer function matrix $K=G(0)$ of a MIMO plant, pair the inputs and outputs of the system based on RGA and evaluate the stability of the closed-loop stability of the chosen pair configurations.
> 
$$K=G(0)=\begin{bmatrix}\frac{5}{3}&1&1\\1&\frac{1}{3}&1\\1&1&\frac{1}{3}\end{bmatrix}$$

> 1. **Calculate the RGA matrix**
$$\Lambda_{ss}(K)=K\odot K^{-T}\\=\begin{bmatrix}\frac{5}{3}&1&1\\1&\frac{1}{3}&1\\1&1&\frac{1}{3}\end{bmatrix}\begin{bmatrix}6&-\frac{9}{2}&-\frac{9}{2}\\-\frac{9}{2}&3&\frac{9}{2}\\-\frac{9}{2}&\frac{9}{2}&3\end{bmatrix}\\=\begin{bmatrix}10&-\frac{9}{2}&-\frac{9}{2}\\-\frac{9}{2}&1&\frac{9}{2}\\-\frac{9}{2}&\frac{9}{2}&1\end{bmatrix}$$

> 2. **Try Configuration 1-1, 2-2, 3-3**

Since $K_{22}$ and $K_{33}$ are perfectly 1, we pair $u_2$-$y_2$ and $u_3$-$y_3$. Although $K_{11}$ seems a little bit deviated from 1, we have no choice but to select $u_1$-$y_1$

Next step is to calculate the Niederlinski's index. Since the input-output pairing is 11,22,33, the selected transfer function elements are already on the diagonal, so there's no need to shift the rows.
$$\mathrm{NI}=\frac{|K|}{\prod_{i=1}^n K_{ii}}=\frac{-\frac{4}{27}}{\frac{5}{3}\times\frac{1}{3}\times\frac{1}{3}}=-\frac{4}{5}<0$$
The index is smaller than 0, so this configuration is always closed-loop unstable and thus infeasible. We need to find another solution.

> 3. **Try Configuration 1-1, 2-3, 3-2**

Switch the second and third rows (or columns) to move the $K_{23}$, $K_{32}$ elements to the diagonal. Calculate the NI based on the new transfer function matrix.
$$K=\begin{bmatrix}\frac{5}{3}&1&1\\1&1&\frac{1}{3}\\1&\frac{1}{3}&1\end{bmatrix}$$
$$\mathrm{NI}=\frac{|K|}{\prod_{i=1}^n K_{ii}}=\frac{\frac{4}{27}}{\frac{5}{3}\times1\times1}=\frac{4}{45}>0$$
This configuration is acceptable because it **may** exist a closed-loop stable controller set for it.


---
## Example - Decoupling for Plant with Delay

> [!NOTE] Question
> Design a decoupler $W(s)$ for the following transfer function matrix with delay
> $$G(s)=\frac{1}{s+1}\begin{bmatrix}(s+2)e^{-3s}&(s+3)e^{-2s}\\e^{-2s} &(s+2)e^{-s}\end{bmatrix}$$

The system delays should be considered in the formation of desired decoupled plant $G_{des}(s)$. We can choose $G_{des}(s)=e^{-3s}I$ to cover the longest delay.
$$G(s)W(s)=G_{des}(s)=\begin{bmatrix}e^{-3s}&\\&e^{-3s}\end{bmatrix}$$
Then the decoupler can be calculated by inverse
$$\begin{align}W(s)&=G^{-1}(s)G_{des}(s)=\frac{adj(G(s))}{|G(s)|}G_{des}(s)\\&=\frac{\begin{bmatrix}(s+2)e^{-s}& -(s+3)e^{-2s}\\-e^{-2s}&(s+2)e^{-3s}\end{bmatrix}}{(s+2)^2e^{-4s}-(s+3)e^{-4s}}\begin{bmatrix}e^{-3s}&\\&e^{-3s}\end{bmatrix}\\&=\frac{1}{(s^2+3s+1)}\begin{bmatrix}(s+2)&-(s+3)e^{-s}\\-e^{-s}&(s+2)e^{-2s}\end{bmatrix}\end{align}$$
The controller matrix could be selected as
$$K(s)=\begin{bmatrix}K_1(s)&0\\0&K_2(s)\end{bmatrix}$$Then the two controller $K_1(s), K_2(s)$ can be designed independently