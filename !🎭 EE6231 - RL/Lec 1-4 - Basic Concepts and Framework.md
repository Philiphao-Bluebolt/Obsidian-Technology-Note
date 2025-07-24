
+ **Notes**
	+ [Basic Concepts of Markov Decision Process](#Basic%20Concepts%20of%20Markov%20Decision%20Process)
	+ [Bellman Equation](#Bellman%20Equation)
	+ [Solving the Bellman Equation](#Solving%20the%20Bellman%20Equation)
	+ [[#]]


+ **Lectures**
	+ [Lec 1](#Lec%201) - **Basic Concepts for RL**
	+ [Lec 2](#Lec%202) - **State Values and the Bellman Equation**
	+ [Lec 3](#Lec%203) - **Optimal State Values and Bellman Optimality Equation**
	+ [Lec 4](#Lec%204) - **Value Iteration and Policy Iteration**
	+ [Questions](#Questions)



---
## Basic Concepts of Markov Decision Process

Reinforcement Learning borrows the concepts from Markov Decision Process, such as state, action, transition, and reward. One of the significant property of MDP is **Memorylessness**, meaning that the past states on the trajectory would not affect future decision $\mathbb{P}(a|s)$, reward $\mathbb{P}(r|s,a,s')$ the transition $\mathbb{P}(s'|a,s)$

The following concepts are based on simple grid world. They are feasible for all reinforcement learning methods and algorithms but may be slightly different for continuous state and action spaces.

+ **Discrete state and action spaces** - the state and action spaces are discrete and thus countable, meaning that expectations regarding states and actions can be calculated by sum rather than integral.


> **State** - $s\in\mathcal{S}$

The state is usually a vector of features describing the current condition of an agent. In the reinforcement learning process, the agent frequently transitions between different state. The continuous transition between states create a **trajectory**

+ $\mathcal{S}$ - **State space** (the set of all possible agent states in the environment)
+ $s$ - One of the states in $\mathcal{S}$
+ $S_t$ - The agent state at time $t$ 


> **Action** - $a\in\mathcal{A}$

The action is the agent's take to transition between states. The transition from a state $s$ to another state $s'$ after taking an action $a$ is usually a stochatic process defined by the transition probability  function $\mathbb{P}(s'|s,a)$

+ $\mathcal{A}$ - **Action space** (the set of all possible agent actions)
+ $a$ - One of the actions in $\mathcal{A}$
+ $A_t$ - The chosen action at time $t$ 


> **Policy** - $\pi(s)$

The policy is a mapping from the state space to the action space ($\pi: \mathcal{S} \to \mathcal{A}$), it determines the choice of action based on the current state. The two kinds of policies are deterministic policy and stochastic policy.

+ **Deterministic (Greedy) policy** $\pi(s)$ - always choose a specific action at a state
$$\pi(s)=a$$
+ **Stochastic (Soft) policy** $\pi(a|s)$ - there's possibility for any action to be chosen
$$\pi(a|s)=\mathbb{P}(A_t=a|S_t=s)$$

> **Reward** - $r(s,a,s')$

The reward is a function of the state-action transition and is jointly determined by the current state $S_t$, the current action $A_t$, and the next state $S_{t+1}$. It's the task specific feedback that guides the agent's policy optimization. 
$$r=f(s,a,s')$$

The cumulated reward on a trajectory, either discounted or not, is defined as the **return** $G$ of the trajectory. Future returns are unknown due to the diversity of trajectories, but their expectation can be calculated.


> **Value** - $v_\pi(s), q_\pi(s)$

The value of a policy is the **mathematical expectation** of all the possible future returns (the sum of current reward and the future discounted rewards). Values are always defined with respect to a policy. There're two types of values, state value and action value.

The discounted factor $\gamma$ reduces the weight of future rewards on the current value.

+ **State Value** $v_\pi(s)$ - the expected return of the current state, considering all the possible actions
$$v_\pi(s)=\mathbb{E}_\pi[G_t|S_t=s]=\sum_{a}\pi(a|s)(\sum_r\mathbb{P}(r|s,a,s')r+\sum_s'\mathbb{P}(s'|s,a)v_\pi(s'))$$
+ **Action Value** $Q_\pi(s,a)$ -  the expected return of the current chosen **state-action pair**
$$q_\pi(s,a)=\mathbb{E}_\pi[G_t|S_t=s,A_t=a]=\sum_r\mathbb{P}(r|s,a,s')r+\sum_s'\mathbb{P}(s'|s,a)v_\pi(s')$$

---
## Bellman Equation

The Bellman Equation (BE) is the expanded form of the state value defintion. It highlights the fact that every state value is depended on another state value. When written in the full matrix form, it can be solved by matrix inversion or iteration.

+ **Elementwise Form**
$$\color{#1E90FF}v_\pi(s)\color{black}=\mathbb{E}_\pi[G_t|S_t=s]=\sum_{a}\pi(a|s)[\sum_r\mathbb{P}(r|s,a)r+\sum_s'\mathbb{P}(s'|s,a)\color{#1E90FF}v_\pi(s')\color{black}]$$
+ **Matrix From** ($n$ state in total)
$$v_\pi=$$

$$\begin{bmatrix}v_\pi(s_1)\\v_\pi(s_2)\\\vdots\\v_\pi(s_n)\end{bmatrix}=$$



---
## Solving the Bellman Equation 




---
## Questions

> **(Lec 1) Since Markov Decision Process assumes memoryless transition and reward, if there's a scene where the agent cannot enter a specific state after entering another state or after a period of time, can this scene be modelled as a MDP?**

If you augment the state space to include the closing-state condition or the time step as an element, this environment would become memoryless again and thus can be described by a MDP.

> **(Lec 2) Since the reward is determined by the current state $s$, action $a$ and the next state $s'$, why does the BE in the slide only has $p(r|s,a)$ rather than $p(r|s,a,s')$**




> **(Lec 2) What is the meaning of *Bootstrapping*?**

*Bootstrapping* originally means to obtain something from itself rather than relying on the external source. In the context of reinforcenment learning, bootstrapping refers to the trick of obtaining the estimation of values using either the Bellman optimization equation or sampling returns. For example, the Bellman Equation is a Bootstrapping method, in which the next state value is used to calculate the current state value and both are estimated.

> **(Lec 2) Why is the reward yields by the current state $S_t$ and action $A_t$ denoted $r_{t+1}$ with the time step number plused by 1**

This is actually owing to the convention dividing action steps in a learning process. In the cycle of RL, the reward together with the state observation are feedback from the environment after the agent's action, so the yielded reward is typically considered part of the next time step rather than the current one. 

![](Pasted%20image%2020250722120220.png)


> **(Lec 2) Why doe we use $s,a,s'$ as the abbreviations of $S_t=s,A_t=a,S_{t+1}=s'$**

Since the MDP is memoryless, the time shift never changes the probability distribution model of reward and transition, meaning that
$$\mathbb{P}(r|S_t=s,A_t=a,S_{t+1}=s')=\mathbb{P}(r|S_{t\color{red}+k}=s,A_{t\color{red}+k}=a,S_{t\color{red}+k\color{black}+1}=s')=\mathbb{P}(r|s,a,s')$$
$$\mathbb{P}(s'|S_t=s,A_t=a)=\mathbb{P}(s'|S_{t\color{red}+k}=s,A_{t\color{red}+k}=a)=\mathbb{P}(s'|s,a)$$
So we don't need to care **WHAT TIME IS IT NOW** and prefer to drop those annoying time step from the denotion for the sake of simplicity.


> **(Lec 4) What is the essential difference between policy iteration and value iteration? They seem to share the same training scheme.**

Value iteration algorithm uses the iterative solution of the **Bellman optimality Equation** to repeatedly update the estimation of state values starting from an initial guess $V_0$. The policy $\pi$ becomes optimal once the estimated value reaches its optimal. Policy iteration

1. **Use of Equations** - value iteration only uses **BOE** but policy iteration uses both **BOE** and **BE**

2. **Policy Implicitness vs Explicitness** - the policy in value iteration is not explicitly stored in the iteration process. The **BOE** only updates the value.

3. **True State Value** - the state value in Value iteration is **not** the true state value since it's just an iterative variable derived from the BOE and not a root of the **BE**. Only the final converged state value is the true state value of the optimal policy. However, the state value in Policy iteration is true since the algorithm would compute a converged true state value using the **BE** for every tried policy.

> **(Lec 4) The other literature (and ChatGPT) says that value iteration doesn't store policy while iterating, why does the pseudo-code example in slide P26 has policy stored**

The value iteraion algorithm has two forms. 

+ **The classical form** - only use the BOE to iteratively update the estimated state value until the optimal true value and the corresponding policy is obtained.
+ **The modified form** - use BOE to update the estimated state value and use the **current** optimal policy to update the value

---
## Slides

### Lec 1

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%201.pdf)

### Lec 2 

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%202.pdf)

### Lec 3

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%203.pdf)

### Lec 4 

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%204(4).pdf)