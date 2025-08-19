
+ **Notes**
	+ [From Discrete Functions to Continuous Functions](#From%20Discrete%20Functions%20to%20Continuous%20Functions)
	+ [Approximator Types](#Approximator%20Types)
	+ [State Value Objective Function](#State%20Value%20Objective%20Function)
	+ [Parameter Update](#Parameter%20Update)
	+ [Sarsa and Q-learning](#Sarsa%20and%20Q-learning)
	+ [Deep Q-learning](#Deep%20Q-learning)

+ **Lectures**
	+ [Lec 8](#Lec%208) - Value Function Methods
	+ [Lec 9](#Lec%209) - Policy Gradient Methods
	+ [Lec 10](#Lec%2010) - Actor-Critic Methods

---
## From Discrete Functions to Continuous Functions

Using tables to store values and policies is intuitive and convenient. However, the tabular method has some critical drawbacks when applying to continuous state and action spaces:

+ **Curse of Dimensionality** - the required memory increases exponentially with larger state and action spaces
+ **Discrete Hypothesis** - tabular storage assumes that both state and action spaces are discretized
+ **Poor Generalization** - the cells of the table have to be updated one by one, which greatly slows down the learning process

In a mathematical viewpoint, a table is just a discrete function with either one or two variables. Intuitively, we can move from this discrete function to a **parameterized continuous function** for a more efficient representation of values and policies.
$$a=\pi(s;w)\quad v=v_\pi(s;w)$$
+ $s$ - variable representing the states
+ $w$ - parameters that make the function trainable

While training, the continuous function works as an **approximator** to the true value $v_\pi(s)$ or policy $\pi(a|s)$, the parameters would be updated by sampling.

---
## Approximator Types

The value or policy function $g(s;w)$ can either be a linear function or a nonlinear function from the prospective of parameters $w$. Nonlinear value or policy functions are usually represented by a neural network.

> **Linear Function** - comprises of two vectors, the **parameter vector** $w$ and the **state basis function vector** $F(s)$. The former is a set of trainable parameters and the latter are functions of state with many possible forms.
$$g(s;w)=w^TF(s)=\begin{bmatrix}w_1&w_2&\cdots\end{bmatrix}\begin{bmatrix}f_1(s)\\f_2(s)\\\vdots\end{bmatrix}$$

> **Nonlinear Function** - usually represented by neural network, would be further discussed in [Part 4](Lec%2011-12%20-%20Value%20and%20Policy%20as%20Neural%20Network.md)(Value and Policy as Neural Network)

---
## State Value Objective Function

The target of state value approximation is to minimize the objective function, which measures the mean square error between the true value function and the approximator function. The sum of error is weighted by the stationary state distribution $d(s)$
$$\begin{align}J(w)&=\mathbb{E}_{s\sim d}[v_\pi(s)-\tilde{v}_\pi(s;w)]^2\\&=\sum_{s\in\mathcal{S}}d_\pi(s)[v_\pi(s)-\tilde{v}_\pi(s;w)]^2\end{align}$$

> **Stationary State Distribution** - evaluates the importance of a state, which is simply the frequency of the state to appear in former trajectories.
$$d_\pi(s)=\frac{n_\pi(s)}{\sum_{s'\in\mathcal{S}}n_\pi(s')}$$

In real implementation, the unknown true value function $v_\pi(s)$ is replaced by the current **expected sampled return** $\mathbb{E}_\pi(R_t|s)$ estimation either by MC(Monte-Carlo) or TD(Temporal Difference)
$$J(w)=\mathbb{E}_{s\sim d}[\mathbb{E}_\pi(R_t|s)-\tilde{v}_\pi(s;w)]^2$$
$$v_\pi(s)\approx \mathbb{E}_\pi(R_t|s)=\begin{cases}\mathbb{E}(G_{t:T}|s)&\mathrm{MC}\\\mathbb{E}(G_{t:t}|s)&\mathrm{TD}\end{cases}$$

---
## Parameter Update





---
## Sarsa and Q-learning 



---
## Deep Q-learning




---
## 


---
## Questions

> **Why do we use a Stationary State Distribution when estimating value function? Isn't every state considered equally in the true value function?**
 
> **What does the equation $d_\pi^T=d_\pi^T P_\pi$ mean?** 





---
## Slides

### Lec 8

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%208(1).pdf)

### Lec 9

![](67795067.pdf)

### Lec 10

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%2010.pdf)