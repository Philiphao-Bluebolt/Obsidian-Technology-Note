+ **Goal** - classify a group of image based on the object or feature in them


+ **Image Similarity and Object Recognition** - Similarity-based Classifier
	+ [[#Template Matching]]
	+ 
+ **Maximum a Posterior (MAP)** - Random-based Classifier
	+ [[#Bayesian Inference]]
	+ [[#MAP-based Classifier]]
	+ [[#Statistical Estimation]]


---
## Template Matching

+ **Goal** - measure the similarity of two images
+ **Measurement** - Eucliean distance, 

When operating object recognition, we compare two images and measure how similar they are. For convenience, all pixels in a $m\times n$ image are rewritten as a $m\times n$ dimension vector.


The correlation coefficient of images $f$ and $g$ is one of the measurement of similarity 

+ **Correlation Coefficient**
$$\gamma=f_nT=\frac{}{}$$




---
## Classifier



---
## Bayesian Inference

+ **Goal** - (MAP) make the decision based on the highly posterior possibility 
+ **Challenge** - likelihood is unknown (can be estimated by [[#Statistical Estimation Problem|Statistical Estimation]])

Bayesian Inference always chooses the class $\omega_i$ with the highly **posterior possibility** $p(\omega_i|x)$ of all the classes $\{\omega_1,\omega_2,\cdots,\omega_n\}$
$$\omega_k=\mathrm{arg}\max_{\omega_i} \{p(\omega_i|x)\}$$
The posterior possibility is not explicitly shown but can be yielded by Bayesian Theorem which combines the new observation $x=x_p$ with the old knowledge $p(\omega_i)$

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
> + **Prior** $p(\omega_i)$ - **(Known)** possibility of each decision $\omega_i$ before knowing $x$
> + **Evidence** $p(x)$ - the possibility of observation $x$ to appear, **not important** to the problem because it's the same for all $\omega_i$ decisions

Only likelihood and prior possibility **differ** the posterior of different classes $\{\omega_1,\omega_2,\cdots,\omega_n\}$

+ **Prior** acts as a **constant** in the posterior function of a specific class $\omega_i$ beacuse it's already known
+ **likelihood** is the most significant part and usually obtained by **statistical estimation** using samples of $x$

The **discriminant function** of a class $\omega_i$ is defined with only the prior and likelihood
$$g_i(x)=\ln p(x|\omega_i)+\ln p(\omega_i)$$

---
## MAP-based Classifier

+ **Hypothesis** - Likelihood is a **Gaussian** distribution of $x$

Assume that the likelihood $p(x|\omega_i)$ of a specific class $\omega_i$ is a multivariable Gaussian distribution, the 



---
## Statistical Estimation

+ **Goal** - estimate the likelihood in MAP



