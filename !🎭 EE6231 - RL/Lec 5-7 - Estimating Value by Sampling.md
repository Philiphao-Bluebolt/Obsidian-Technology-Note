
+ **Notes**

+ **Lectures**
	+ [Lec 5](#Lec%205) - Monte Carlo Methods
	+ [Lec 6](#Lec%206) - Stochastic Approximation
	+ [Lec 7](#Lec%207) - Temporal-Difference Methods


---
## Monte Carlo Methods


---
## Questions

> **(Lec 5) What is the difference between first visit MC and every visit MC?**

If a state $s$ is visited multiple times in a episode, the first visit MC will only consider the return from the first visit while every visit MC will consider the return of every visit.

> **(Lec 6) Why is the Monte-Carlo method a offline algorithm? Can't we dynamically update the average just like TD?**



> **(Lec 7) Why does the TD uses next Q value to update the current Q value? Usually Q value is defined as the expectation of the next V value over the returns**

Although this update method is not intuitive by definition, it's actually practical to do so. The transition between states can be viewed as a graph where states are nodes and actions are links. Since the current state-action pair $(S_t,A_t)$ leads to a few next states and a state value $v_\pi(S_{t+1})$ is defined as the average over all its possible action values, updating the current action value by the next action value actually "gives credit to" the current action **link**.






---
## Slides


### Lec 5

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%205(3).pdf)


### Lec 6

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%206(1).pdf)


### Lec 7

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%207(2).pdf)

![](PPT_Reinforcement_Learning_NTU_2025_v1_0_Lecture%207b.pdf)


