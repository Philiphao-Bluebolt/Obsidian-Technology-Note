The assignment's question is to obtain the optimal policy navigating on a simple $2\times2$ grid world. Since the model of the environment, which comprises the reward probability function and the transition probability function, is known, the Value Iteration and Policy Iteration methods can be used to get the answer.

## Preparations

+ **State Transition Table** - records all the transition probability given a state $s$ and an action $a$. In this deterministic grid world, the next state is completely determined by the current state $S_t$ and chosen action $A_t$
$$\sum_{s'}\mathbb{P}(s'|s,a)v(s')=s'_{s,a}$$

|       |   $a_1$   |   $a_2$   |   $a_3$   |   $a_4$   |   $a_5$   |
| :---: | :-------: | :-------: | :-------: | :-------: | :-------: |
| $s_0$ |   $s_0$   |   $s_1$   |   $s_2$   |   $s_0$   |   $s_0$   |
| $s_1$ | $s_1$<br> | $s_1$<br> |   $s_3$   |   $s_0$   | $s_1$<br> |
| $s_2$ | $s_0$<br> | $s_3$<br> | $s_2$<br> | $s_2$<br> | $s_2$<br> |
| $s_3$ | $s_1$<br> | $s_3$<br> | $s_3$<br> | $s_2$<br> | $s_3$<br> |

## Value Iteration

The main idea of value iteration is based on the iterative solution of the **Bellman Optimality Equation**. The policy in this method is usually implicit and only the value is continuously updated.

+ **Policy Update** - choose the best action on every state
$$\pi_{k+1} = \arg\max_{\pi} \left( r_{\pi} + \gamma P_{\pi} v_{\pi_k} \right)$$
+ **Value Update** - based on the last policy
$$v_{k+1} = \max_{\pi} \left( r_{\pi} + \gamma P_{\pi} v_{\pi_k} \right)$$
## Policy Iteration

The Policy Iteration makes use of both the **Bellman Optimality Equation** and **Bellman Equation** in the iterations. For every policy, an accurate value is obtained.

+ **Policy Evaluation** - the policy stays unchanged and an accurate estimation of the current value is obtained through iteration on the **Bellman Equation** until it converged.
$$v_{\pi_k}^{(j+1)}=r_{\pi_k}+\gamma P_{\pi_k}v_{\pi_k}^{(j)} \quad j=0,1,2$$

+ **Policy Improvement** - always choose the best action on every state
$$\pi_{k+1} = \arg\max_{\pi} \left( r_{\pi} + \gamma P_{\pi} v_{\pi_k} \right)$$

## The Result

The result of the Python program is shown in the graph below. Although the optimal policies given by the two method is different, they're both valid because the optimal policy is not unique. 

![](Pasted%20image%2020250713232858.png)
## Multianswer Explanation

Since the environment is small, the optimal policy can be intuitively recognized. The desired policy should make all the greedy actions pointing to the top-left $s_0$. The reward doesn't define constraint zone or penalize the out-of-border action, so the optimal policy isn't unique.

All the valid optimal action are shown in the following image.

+ $s_3$ can transition to either $s_1$ or $s_2$.
+ $s_1$ and $s_2$ should transition to $s_0$
+ $s_0$ can choose to go up, right, or stay, which all lead to the same grid
![](Pasted%20image%2020250713232354.png)

As a result, all the policies following the action pattern is optimal, yielding more than one answer to the question.

## The Python Code

The following code contains the implementation for both the value iteration and the policy iteration.

+ `__transition()` returns the next state given a current state and the action
+ `__reward()` returns the reward given the current state, the action and the next state
+ `value_iter()` is the value iteration function
+ `policy_iter()` is the policy iteration function

```python
class GridRL():
    def __init__(self):
        '''Grid world initialization
        '''
        self.n_state = 4
        self.n_action = 5
        self.gamma = 0.9

        self.transition_table = [[0, 1, 2, 0, 0],
                                 [1, 1, 3, 0, 1],
                                 [0, 3, 2, 2, 2],
                                 [1, 3, 3, 2, 3]]
        self.action_id = {"up": 0,
                          "right": 1,
                          "down": 2,
                          "left": 3,
                          "stay": 4}

    def __transition(self, state, action):
        '''Return the next state given current state and action
        '''
        action_index = self.action_id[action] if type(action) == type("") else action
        return self.transition_table[state][action_index]
        
    def __reward(self, state, next_state):
        '''Return the reward given current the next states, not a function of action
        '''
        reward = 0
        if state == next_state: reward += -0.5
        if next_state == 0: reward += 10 # Reach the goal
        else: reward += -1
        return reward

    def value_iter(self):
        '''Value iteration algorithm
        '''
        policy = [0 for _ in range(self.n_state)]
        q_value = [[0 for _ in range(self.n_action)] for _ in range(self.n_state)]
        v_value = [0 for _ in range(self.n_state)]
        last_v_value = v_value
        
        # Value Convergence Control
        v_diff = 1000
        v_diff_th = 0.0001
        cnt = 0

        while v_diff > v_diff_th:

            # Policy update by BOE
            for i_state in range(self.n_state):
                for i_action in range(self.n_action):
                    next_state = self.__transition(i_state, i_action)
                    q_value[i_state][i_action] = self.__reward(i_state, next_state) + self.gamma * v_value[next_state]

                # Detail: The action with the smallest index would be chosen if there're more than one maximum Q value
                policy[i_state] = q_value[i_state].index(max(q_value[i_state])) 
            
            # Value update by BOE
            last_v_value = v_value
            for i_state in range(self.n_state):
                next_state = self.__transition(i_state, policy[i_state])
                v_value[i_state] = self.__reward(i_state, next_state) + self.gamma * last_v_value[next_state]
            
            # Calculate value difference
            v_diff = sum([abs(x-y) for x, y in zip(last_v_value, v_value)]) / self.n_state
            cnt += 1

        return policy, v_value
            
    def policy_iter(self):
        '''Policy iteration algorithm
        '''
        policy = [0 for _ in range(self.n_state)]
        last_policy = [1 for _ in range(self.n_state)] # Prevent Jumping out at the first step
        q_value = [[0 for _ in range(self.n_action)] for _ in range(self.n_state)]
        v_value = [0 for _ in range(self.n_state)]
        last_v_value = v_value
    
        # Value Convergence Control
        v_diff = 1000
        v_diff_th = 0.0001
        cnt = 0

        while last_policy != policy:
            
            # Value update by BE
            v_diff = 1000
            while v_diff > v_diff_th:
                last_v_value = v_value
                for i_state in range(self.n_state):
                    next_state = self.__transition(i_state, policy[i_state])
                    v_value[i_state] = self.__reward(i_state, next_state) + self.gamma * last_v_value[next_state]
                v_diff = sum([abs(x-y) for x, y in zip(last_v_value, v_value)]) / self.n_state
            
            # Policy update by BOE
            last_policy = policy
            for i_state in range(self.n_state):
                for i_action in range(self.n_action):
                    next_state = self.__transition(i_state, i_action)
                    q_value[i_state][i_action] = self.__reward(i_state, next_state) + self.gamma * v_value[next_state]

                # Detail: The action with the smallest index would be chosen if there're more than one maximum Q value
                policy[i_state] = q_value[i_state].index(max(q_value[i_state])) 
            
            cnt += 1

        return policy, v_value

if __name__ == "__main__":
    grl = GridRL()
    print(grl.value_iter())
    print(grl.policy_iter())

```


