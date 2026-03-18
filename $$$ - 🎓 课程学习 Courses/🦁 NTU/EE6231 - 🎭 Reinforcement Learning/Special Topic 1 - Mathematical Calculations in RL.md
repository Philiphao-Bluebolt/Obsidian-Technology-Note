Here we further discuss the mathematical principles of RL, including proofs and calculation details.

+ **Part 1 - Model Based** 
	+ Lec 2 - [Elementwise Bellman Equation](#Elementwise%20Bellman%20Equation)
	+ Lec 2 - [Matrix Bellman Equation](#Matrix%20Bellman%20Equation)
	+ Lec 3 - [Iterative Solution of Bellman Equation](#Iterative%20Solution%20of%20Bellman%20Equation)
	+ Lec 3 - 
+ **Part 2 - Tabular Sampling**
	+ Lec 5 - 
	+ Lec 5 - 
+ **Part 3 - Function Approximation**
	+ Lec 8 - [Proof - Stationary State Distribution](#Proof%20-%20Stationary%20State%20Distribution)
	+ Lec 9 - 
+ **Part 4 - Neural Network**


---
## Elementwise Bellman Equation 

The state value $v_\pi(s)$ is defined as the expectation of all the possible future trajectory returns. 
$$\begin{align}v_\pi(s)&=\mathbb{E}_\pi[G_t|S_t=s]\\&=\mathbb{E}_\pi[r_{t+1}+\gamma G_{t+1}|S_t=s]\end{align}$$
Mathematical Expectation is a linear operation, thus the state value can be seperated to the sum of two terms, the **state average reward** and the **average next discounted return**
$$\begin{align}v_\pi(s)&=\mathbb{E}_\pi[G_t|S_t=s]\\&=\mathbb{E}_\pi[r_{t+1}+\gamma G_{t+1}|S_t=s]\\&=\color{#1E90FF}\mathbb{E}_\pi[r_{t+1}|S_t=s]\color{black}+\color{#BA55D3}\gamma\mathbb{E}_\pi[G_{t+1}|S_t=s]\end{align}$$
Notice that the reward yielded by the current state-action pair is considered part of the next time step with denotion $r_{t+1}$ rather than $r_t$. 

+ **Abbreviation**
$$s,a,s' \to S_t=s,A_t=a,S_{t+1}=s'$$

+ **Model and Policy**
$$\pi=\pi(a|s)\quad p_{s'}=\mathbb{P}(s'|s,a)\quad p_r=\mathbb{P}(r|s,a,s')$$

+ **Learning Scheme**
$$s\xrightarrow{\pi(a|s)}s,a\xrightarrow{\mathbb{P}(s'|s,a)}s,a,s'\xrightarrow{\mathbb{P}(r|s,a,s')}s,a,s',r$$

The calculates below make use of the **[Law of Total Expectation](均值与方差%20Mean%20&%20Variance.md#总期望定律%20Law%20of%20Total%20Expectation)** in Probability Theory. This law shows how to expand an expectation formula $\mathbb{E}(X)=\mathbb{E}[\mathbb{E}(X|Y)]$


> **1. Current State Average Reward**

The expected reward of the current state $s$ averages over **two** probability functions, the reward distribution model $\mathbb{p}(r|s,a)$ and the policy $\pi(a|s)$
$$\begin{align}\mathbb{E}_\pi[r_{t+1}|S_t=s]&=\mathbb{E}_\pi[\mathbb{E}_{r\sim p_r}(r|s,a)]\\&=\sum_a\pi(a|s)\mathbb{E}_{r\sim p_r}(r|s,a)\\&=\sum_a\pi(a|s)\sum_r \mathbb{P}(r|s,a)r\end{align}$$
> **2. Average Next Discounted Return**

Beware of the nested conditional probability here. The expected next return under the current state averages over three probability functions, the probability function of the next return $\mathbb{P}(G_{t+1}|s,a,s')$, the transition probability $\mathbb{P}(s'|s,a)$, and the policy $p(a|s)$
$$\gamma\mathbb{E}_\pi[G_{t+1}|S_t=s]=\gamma\mathbb{E}\{\mathbb_{E}[\mathbb{E}()]\}$$



---
## Matrix Bellman Equation





---
## Iterative Solution of Bellman Equation


---
## Proof - Stationary State Distribution

Here we prove that the SSD only depends on the MDP transition probability and the policy.