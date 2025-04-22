+ **Goal** - Improve the performance of machine learning by reducing data dimension

Datasets with large dimension are common in the realm of machine learning. However, the "Curse of Dimension" usually impairs the performance of the algorithms in the following aspects:

+ Increase Computational Complexity 
+ Reduce the Sample-Parameter Ratio (by increasing number of parameters)

One of the methods to reduce dimension is to select a subset of the most relevant and least redundant features, which is the process of **Feature Selection**

+ **Individual Evaluation**

+ 




---
## Peaking Phenomenon

+ **Goal** - Describes the relationship of feature number and performance
+ **Conclusion** - Smaller dataset should have less features

The Peaking Phenomenon shows that the performance of a machine learning algorithm reaches its peak for a certain dimension $l$ but rapidly declines when the feature number becomes too high.

Smaller dataset has a smaller optimal dimension and performance, thus the feature number should be lower for small data.

![](Pasted%20image%2020250415160022.png)

---
## Individual Feature Evaluation

+ **Goal** - Individually check the label relevance of a feature
+ **Method** - Fisher's Ratio (Continuous), Mutual Information (Discrete)

Individual Feature Evaluation methods

### Fisher's Ratio

Fisher's Ratio is 



### Mutual Information


---
## 