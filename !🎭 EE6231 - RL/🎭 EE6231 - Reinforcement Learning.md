Given by Professor Wen Fuxi, this course introduces the basic concepts, algorithms, tricks, and frontiers of reinforcement learning.

+ [Part 1](#Part%201%20-%20Basic%20Concepts%20and%20Framework%20(Lec%201-4)) - **Basic Concepts and Framework** (Lec 1-4) - [Note](Lec%201-4%20-%20Basic%20Concepts%20and%20Framework.md)
+ [Part 2](#Part%202%20-%20Estimating%20Values%20by%20Sampling%20(Lec%205-7)) - **Estimating Value by Sampling** (Lec 5-7) - [Note](Lec%205-7%20-%20Estimating%20Value%20by%20Sampling.md)
+ [Part 3](#Part%203%20-%20Continuous%20Value%20and%20Policy%20(Lec%208-9)) - **Value and Policy as Continuous Function** (Lec 8-10) - [Note](Lec%208-10%20-%20Value%20and%20Policy%20as%20Continuous%20Function.md)
+ [Part 4](#Part%204%20-%20Value%20and%20Policy%20as%20Neural%20Network%20(Lec%2011-12)) - **Value and Policy as Neural Network** (Lec 11-12) - [Note](Lec%2011-12%20-%20Value%20and%20Policy%20as%20Neural%20Network.md)

+ [CA](CA%20-%20Optimal%20Policy%20of%20a%20Grid%20World.md) - **Optimal Policy of a Grid World**

---
## Part 1 - Basic Concepts and Framework (Lec 1-4)

This part of the lecture covers the basic concepts of reinforcement learning, including the concepts of Markov Decision Process, which describes the interactive environment, and the framework of model-based reinforcement learning, which is the alternating iteration of updating value of the states and the current policy.

> **Lec 1 (Basic Concepts for RL)** - serves as an opening introduction of the whole course and the reinforcement learning technology, discussing the history, applications, challenges and basic concepts of RL. The concepts are borrowed from **Markov Decision Process**, assuming memorylessness.

> **Lec 2 (State Values and the Bellman Equation)** - introduces return, value, and the Bellman Equation, which builds the connection between the value of different states. It's proved that all the state values can be solved by the **matrix-form** Bellman Equation if the environment model, comprising the reward and transition probabilities, is known.

> **Lec 3 (Optimal State Values and Bellman Optimality Equation)** - gives the definition of optimal value and policy, which is the target of RL. If the model is known, the optimal values can be calculated using the BOE in a iterative manner based on **Contraction Mapping Theorem**. The optimal policy simply maximizes every action values.

> **Lec 4 (Value Iteration and Policy Iteration)** - introduces the frameworks of two RL optimization algorithms based on the alternating updates of policy and value using the BE and the BOE. It's of great important to distinguish the **difference** between value iteration and policy iteration.

---
## Part 2 - Estimating Value by Sampling (Lec 5-7)

In the first part, the optimal policy is obtained by iteratively solving BOE and BE, assuming full knowledge of the transition and reward probability model. However, its's difficult to  accurate 

> **Lec 5** - 




---
## Part 3 - Value and Policy as Continuous Function (Lec 8-9)





---
## Part 4 - Value and Policy as Neural Network (Lec 11-12)