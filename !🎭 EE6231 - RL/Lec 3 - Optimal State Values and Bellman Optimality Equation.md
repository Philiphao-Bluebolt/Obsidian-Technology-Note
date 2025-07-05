
Bootstrapping?

Optimal State Values
Optimal Policy

Bellman Optimality Equation


$\gamma$ the decaying ratio

$v_\pi(s_i)$ is the state value of a state $s_i$ under the policy $\pi$ which is determined by the current reward $r_i$ and a discounted future value $\gamma v_\pi(s_f)$

$q(s_i,a)$ is the action value (a function of the state-action pair)

---
## Optimal Policy

The current state value $v_\pi(s)$ can decide if a policy $\pi$ is good or not. Better policy has larger value.

The optimal policy $\pi^*$ has the highest state values for **all the state** $s$ than any other policy.


---
## Bellman Optimality Equation (BOE)

The equation aims to find the largest state value 

Is the optimal policy local or global? I think it's global because the policy describes the choice at any state so the optimal policy can describe the best action at any state.


+ **Elementwise Form**
$$\begin{align}v(s)&=\max_\pi\sum_a\pi(a|s)(\sum_r p(r|s,a)r+\gamma\sum_{s'}p(s'|s,a)v(s')) \quad \forall s \in S\\&=\end{align}$$


+ **Matrix Form**

$$v=\max_\pi(r_\pi+\gamma P_\pi v)$$

Elegent in form but tricky to solve

What is unknown

+ Any future state reward $v(s')$
+ 

---
## BOE Solution

The solution always exists and is unique.



---
## Analyzing

