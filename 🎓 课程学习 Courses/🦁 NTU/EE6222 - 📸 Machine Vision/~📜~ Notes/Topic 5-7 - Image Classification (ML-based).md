+ **Goal** - classify a group of image based on the object or feature in them

+ **Image Similarity and Object Recognition** - Similarity-based Classifier
	+ [[#Template Matching]]
	+ [[#Distance-based Classifier]]
+ **Maximum a Posterior (MAP)** - Random-based Classifier
	+ [[#Bayesian Inference]]
	+ [[#MAP-based Classifier]]
	+ [[#Statistical Estimation]]


---
## Template Matching and Similarity

+ **Goal** - measure the similarity of two images
+ **Measurement** - Euclidean distance (normalized), correlation coefficient (normalized)

When operating object recognition, we compare the input with the template image and measure how similar they are. For convenience, all pixels $f_i$ in the image $f$ are rewritten as a $n$-dimension vector.
$$f=\begin{bmatrix}1&1\\1&0\end{bmatrix}\quad\to\quad f=\begin{bmatrix}1&1&1&0\end{bmatrix}^T$$
The similarity of two images $f$ and $g$  is measured by two metrics in which the denotation $f_n, g_n$ represent **normalized image vectors**

+ **Normalized Euclidean Distance**
$$d_n=(f_n-g_n)^T(f_n-g_n)$$
+ **Correlation Coefficient** ($-1<\gamma<1$)
$$\gamma=f_n^T g_n$$

The normalization of the vector scales the pixels into zero mean and unit variance variables. This is to prevent luminance-related matching errors.

+ **Pixel Mean** $\mu_f$ and **Centralized Vector** $f_c$ 
$$\mu_f=\frac{\sum_{i=1}^n f_i}{n}=\frac{3}{4}$$
$$f_c=\begin{bmatrix}f_1-\mu_f&\cdots&f_n-\mu_f\end{bmatrix}^T=\begin{bmatrix}\frac{1}{4}&\frac{1}{4}&\frac{1}{4}&-\frac{3}{4}\end{bmatrix}^T$$
+ **Pixel Standard Deviation** $\sigma_f$
$$\sigma_{f}=\sqrt{\frac{1}{n}\sum_{i=1}^n (f_i-\mu_f)^2}=\sqrt{\frac{1}{n}f_c^Tf_c}=\frac{\sqrt{3}}{4}$$
+ **Normalized Vector** $f_n$ - zero mean and unit variance 
$$f_n=\frac{f_c}{\sigma_f}=\begin{bmatrix}\frac{f_1-\mu_f}{\sigma_f}&\cdots&\frac{f_n-\mu_f}{\sigma_f}\end{bmatrix}^T$$

---
## Distance-based Classifier



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

+ **Goal** - estimate the **likelihood** in MAP



