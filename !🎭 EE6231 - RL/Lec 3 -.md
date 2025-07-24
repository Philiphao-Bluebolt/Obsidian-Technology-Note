





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


