
+ [Bayesian Inference](#Bayesian%20Inference)
+ 
+ **Examples**
	+ 

---
## Bayesian Inference

+ **Goal** - (MAP) make the decision based on the highly posterior possibility 
+ **Challenge** - likelihood is unknown (can be estimated by Statistical Estimation)

Bayesian Inference always chooses the class $\omega_i$ with the highly **posterior probability** $p(\omega_i|x)$ of all the classes $\{\omega_1,\omega_2,\cdots,\omega_n\}$
$$\omega_k=\mathrm{arg}\max_{\omega_i} \{p(\omega_i|x)\}$$
The posterior probability is not explicitly shown but can be yielded by Bayesian Theorem which combines the new observation $x=x_p$ with the old knowledge $p(\omega_i)$

> [!NOTE] Bayesian Theorem
>+ **1D Form**
> $$p(\omega_i|x)=\frac{p(x|\omega_i)p(\omega_i)}{p(x)}$$
>+ **High Dimension Form** 
> $$p(\omega_i|x)=p(x|\omega_i)p(\omega_i)p^{-1}(x)$$

> [!WARNING] Denotations of the new observation
> + $X$ is the **random variable** that obeys a random distribution $p(x)$
> + $x$ is a **variable** of function $p(\omega_i|x)$ representing a sample from $X$
> + $x_p$ is a specific **sample** from $X$
> 
> The observation can be a scalar or a vector

> [!HINT] Components in the Bayesian Equation
> + **Posterior** $p(\omega_i|x)$ - **(Desired)** a function describing the possibility of $\omega_i$ with different value of $x$ 
$$p(\omega_i)=\int_{-\infty}^{+\infty}p(\omega_i|x)\mathrm{d}x$$
$$\sum_{i=1}^n p(\omega_i|x=x_p)=1$$
> + **Likelihood** $p(x|\omega_i)$ - **(Unknown)** distribution function of $x$ with different value of $\omega$
$$\int_{-\infty}^{+\infty}p(x|\omega_i)\mathrm{d}x=1$$
> + **Prior** $p(\omega_i)$ - **(Known)** probability of each decision $\omega_i$ before knowing $x$
> + **Evidence** $p(x)$ - the probability of observation $x$ to appear, **not important** to the problem because it's the same for all $\omega_i$ decisions

Only likelihood and prior possibility **differ** the posterior of different classes $\{\omega_1,\omega_2,\cdots,\omega_n\}$

+ **Prior** acts as a **constant** in the posterior function of a specific class $\omega_i$ beacuse it's already known
+ **likelihood** is the most significant part and usually obtained by **statistical estimation** using samples of $x$

The **discriminant function** of a class $\omega_i$ is defined with only the prior and likelihood
$$g_i(x)=\ln p(x|\omega_i)+\ln p(\omega_i)$$

---
## MAP Classifiers

+ **Goal** - obtain discriminant functions for every class 

MAP classification law is based on comparisons between different class discriminant functions. This section assumes the knowledge of both prior probability $p(\omega_i)$ and likelihood $p(x|\omega_i)$ of all the classes.

Assume that the likelihood functions $p(x|\omega_i)$ is a $d$-dimension Gaussian distribution describing the probability distribution of features in a specific class, which is usually the case. In real practice, the parameters $\mu_i, \Sigma_i$ are obtained using statistical estimation on a relevant dataset.

+ **Gaussian Likelihood Distribution**
$$p(x|\omega_i)=N(\mu_i, \Sigma_i,x)=\frac{1}{\sqrt{(2\pi)^d|\Sigma_i|}}\exp[-\frac{1}{2}(x-\mu_i)^T\Sigma^{-1}_i(x-\mu_i)]$$

Substitute the likelihood into the distribution functions and get the following. The quadratic term 
$$\begin{align}g_i(x)&=\ln p(x|\omega_i)+\ln p(\omega_i)\\&=\ln\{\frac{1}{\sqrt{(2\pi)^d|\Sigma_i|}}\exp[-\frac{1}{2}(x-\mu_i)^T\Sigma^{-1}_i(x-\mu_i)]\}+\ln p(\omega_i)\\&=\color{DarkOrange}-\frac{1}{2}(x-\mu_i)^T\Sigma^{-1}_i(x-\mu_i)\color{DodgerBlue}-\frac{d}{2}\ln2\pi-\frac{1}{2}|\Sigma_i|+\ln p(\omega_i)\\&=\end{align}$$






---
## Example

