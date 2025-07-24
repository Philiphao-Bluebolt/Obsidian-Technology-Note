
+ **Notes**
	+ [From Discrete Functions to Continuous Functions](#From%20Discrete%20Functions%20to%20Continuous%20Functions)
	+ 

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

In a mathematical viewpoint, a table is just a discrete function with either one or two variables. Intuitively, we can move from this discrete function to a **continuous function** for a more efficient representation of values and policies.
$$a=\pi(s;w)\quad v=v_\pi(s;w)$$
+ $s$ - variable representing the states
+ $w$ - parameters that make the function trainable

While training, the continuous function works as an **approximator** to the true value $v_\pi(s)$ or policy $\pi(a|s)$, the parameters would be updated by sampling.

---
## Approximator Types

The value or policy function $g(s;w)$ usually comprises of two vectors, the parameter vector $w$ and the state feature vector $F(s)$
$$g(s;w)=w^TF(s)=$$





---
##




---
## Questions






---
## Slides

### Lec 8

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%208(1).pdf)

### Lec 9

![](67795067.pdf)

### Lec 10

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%2010.pdf)