
+ **Bayesian Decision**
	+ [Bayes Decision](#Bayes%20Decision)
	+ [Parameter Estimation](#Parameter%20Estimation)
		+ [Single Gaussian Model](#Single%20Gaussian%20Model)
		+ [Gaussian Mixture Model](#Gaussian%20Mixture%20Model)
	+ [Naïve Bayes](#Naïve%20Bayes)
		+ [Gaussian Naïve Bayes](#Gaussian%20Naïve%20Bayes)
		+ [Bernoulli Naïve Bayes](#Bernoulli%20Naïve%20Bayes)
		+ [Multinomial Naïve Bayes](#Multinomial%20Naïve%20Bayes)
+ **Linear Discriminant Analysis**
	+ [Two-class Discriminant Analysis](#Two-class%20Discriminant%20Analysis)
	+ [Multiple Discriminant Analysis](#Multiple%20Discriminant%20Analysis)
+ **Support Vector Machine**
	+ 
+ **Classification Tree**
	+ 
+ **Evaluation**
	+ [Testing Set Hold-out](#Testing%20Set%20Hold-out)
	+ 


---
## Bayes Decision

+ **Goal** - determine the classification based on the MAP
+ **See also** - [Maximum a Posteriori Estimation](Q2%20-%20Maximum%20a%20Posteriori%20Estimation.md)

The Bayes Decision Rule for a classifier is to choose the maximum posterior probability $p(\omega_i|x)$ given a specific value of the evidence $x$
$$\omega(x)=\arg\max_{\omega_i} p(\omega_i|x)=\arg\max_{\omega_i}[\frac{p(x|\omega_i)p(\omega_i)}{p(x)}]$$
To make this comparison possible, we need the **likelihood** probability function $p(\omega_i|x)$ of every class $\{\omega_1, \omega_2,\cdots, \omega_i,\cdots,\omega_n\}$

---
## Parameter Estimation

+ **Goal** - estimate the likelihood function for the Bayes decision

The likelihood in the Bayes formula is usually represented by one or more multivariable Gaussian distribution.

+ **Multivariable Gaussian Distribution** (dimension $d$)
$$p(x|\omega_i)=\mathcal{N}(\mu_i,\Sigma_i)=\frac{1}{\sqrt{(2\pi)^d|\Sigma|}}\exp[-\frac{1}{2}(x-\mu_i)^T\Sigma^{-1}(x-\mu_i)]$$


### Single Gaussian Model






### Gaussian Mixture Model





---
## Naïve Bayes

+ **Assumption** - all the features in the dataset are independent (diagonal covariance matrices)

Naïve Bayes is a simplified version of the Bayes decision assuming independence between all the features in the dataset. This property means that all the covariance matrices are diagonal.

### Gaussian Naïve Bayes




### Bernoulli Naïve Bayes


### Multinomial Naïve Bayes


---
## Two-class Discriminant Analysis



---
## Multiple Discriminant Analysis



---
## Classification Tree



---
## Testing Set Hold-out 


---
## Evaluation Metrics

### 



### 

+ **Accuracy** - correct classification rate
$$\mathrm{Acc}=\frac{TP+TN}{TP+FP+TN+FN}=\frac{\mathrm{True}}{\mathrm{All}}$$
+ **Error Rate** - wrong classification rate
$$\mathrm{Er}=\frac{FP+FN}{TP+FP+TN+FN}=\frac{\mathrm{False}}{\mathrm{All}}$$
+ **Sensitivity / Recall** - positive correct classification rate
$$\mathrm{Sens}=\mathrm{Recall}=\frac{TP}{TP+FN}=\frac{TP}{\mathrm{Positive}}$$
+ **Specificity** - negative correct classification rate
$$\mathrm{Spec}=\frac{TN}{TN+FP}=\frac{TN}{\mathrm{Negative}}$$
+ **Precision** - positive correct classification to all positive prediction
$$\mathrm{Prec}=\frac{TP}{TP+FP}=\frac{TP}{\mathrm{Pos Pred}}$$


