Neural Network is the subfield of Artificial Intelligence and Machine Learning. It can be categoried into two classes, shallow neural network and deep neural network.

+ **Introduction**
	+ [[#Neuron Model]]
	+ [Activation Function](#Activation%20Function)
	+ [Types and Learning Schemes](#Types%20and%20Learning%20Schemes)
+ **Self-Organizing Map (SOM)**
	+ [SOM Architecture](#SOM%20Architecture)
	+ [SOM Training](#SOM%20Training) - [Competition](#Competition) | [Cooperation](#Cooperation) | [Weights Adaptation](#Weights%20Adaptation) | [Phases](#Phases)
+ **Radial Basis Function (RBF)**
	+ [RBF Architecture](#RBF%20Architecture)
	+ [RBF Training](#RBF%20Training)
+ **Support Vector Machines (SVM)**
	+ 
+ **Multilayer Perceptron Neural Networks (MLP)**

+ **Convolution Neural Network (CNN)**

+ **Recurrent Neural Network (RNN)**


---
## Neuron Model

+ **Elements** - Synapses, Adder, Activation Function

The neuron is the fundemantal **unit** of a neural network inspired by the human neuron. Neurons in adjacent layers are connected by weighted connection, describing the strength of each input signal from the last neuron.

![[Pasted image 20241022162827.png]]

---
## Activation Function

The activation function of a neuron introduces nonlinearity to the network and making it capable of representing a nonlinear function (curved surface) rather than only a linear function (hyperplane).

The most popular choice is the ReLu function.

![[Pasted image 20241124151754.png]]

---
## Types and Learning Schemes

There're so many neural networks. Every year, there are new networks invented either by tuning the old architectures or implementing new concepts. All the networks can be categoried in different perspectives

+ **Structure**
	+ Feed-forward - data flows in one direction without any loop
	+ Recurrent - contain loops that help with storing past information
	+ Graph - all the neurons are arranged in a graph
+ **Task**
	+ Supervised - use labelled data (classification, regression)
	+ Unsupervised - use unlabelled data (clustering, association analysis)

There're three different learning rules of neural networks 

+ **Error-correction**
+ **Hebbian**
+ **Competitive**

---
## SOM Architecture

+ **Type** - Unsupervised Learning
+ **Application** - Clustering, Representative Selection, Dimension Reduction

Self-Organzing Map is a unsupervised learning network based on activation, each layer of the network is a 1D or 2D lattice of neurons. The arrangement pattern of neurons is usually square but can be other shape such as hexagon as well.

Each neuron is represented by a weight vector of the size dimension with the input vector. The number of neurons is usually set to the **number of clusterings** or tested to determine.

![](Pasted%20image%2020250504165527.png)

---
## SOM Training

+ **Stage** - Competition, Cooperation, Weight Adaptation
+ **Parameters** - neuron weights

SOM training is made up of three processes: Competition, Cooperation, Weights Adaptation. All the neuron weight vectors are randomly initialized before the processes start.

### Competition

+ **Goal** - decide the center neuron for cooperation

Competition is the process in which all the neurons on the some layer compete to be center of the update neighbourhood when there's a input. The neuron with the **nearest** weight vector to the input $x$ becomes the **only** winner $i$.
$$i(x)=\arg\min_{i\in j}||x-w_j||$$
### Cooperation

+ **Goal** - decide the update factors for update neighbourhood neurons

Cooperation determines the neighbourhood of neurons to be updated in the next adaptation stage as well as the correponding **update factor**. It has the following properties:

> **Distance Decay** - the farther a neuron $j$ is to the center neuron $i$ **spatially**, the smaller its adaptation shift will be. (Usually described by a Gaussian function)
$$h_{ij}=\exp(-\frac{d^2_{ij}}{2\sigma^2})=\exp(-\frac{||r_i-r_j||}{2\sigma^2})$$
> **Time Decay** - the adaptation shift gradually becomes smaller as learning steps $n$ increase. (Usually described by a Gaussian function as well)
$$\sigma(n)=\sigma_0\exp(-\frac{n}{\tau_1})$$

The complete update factors for neighbourhood neurons
$$h_{ij}(n)=\exp(-\frac{d^2_{ij}}{2\sigma^2(n)})=\exp[-\frac{d^2_{ij}}{2\sigma_0^2\exp^2(-\frac{n}{\tau_1})}]$$
### Weights Adaptation

+ **Goal** - update the weight vector of neurons in the cooperation neighbourhood

In this process, the weight vectors of the center and its neighbourhood neurons are shifted towards the current input vector by the following update law.
$$w_j(n+1)=w_j(n)+\eta(n)h_{ji(x)}(n)[x-w_j(n)]$$
> **Learning Rate** - the time decaying factor of updating
$$\eta(n)=\eta_0\exp(-\frac{n}{\tau_2})$$
## Phases

There exists two phases in the SOM adaptive process: Self-organizing and Convergence

> **Self-organizing** (global) - 1000 iterations at least

The initial $\sigma_0$ should be as large as the radius of the lattice (half of the longest distance between neurons). The learning rate $\eta$ should be begin with a value close to 0.1
$$\begin{cases}\sigma_0=\frac{r_\max}{2}\\  \tau_1=\frac{1000}{\ln\sigma_0}\\\eta_0=0.1 \\\tau_2=1000\end{cases}$$
> **Convergence** (local) - 500 times number of neurons at least

The learning rate can be fixed to a small on the order of 0.01. The only updated neuron is the winning center neuron.
$$\sigma(n)=0.1$$


---
## RBF Architecture

+ **Type** - Supervised Learning
+ **Application** - Classification

The Radial Basis Function is a special type of fully connected feed-forward neural network containing only one hidden layer. It has special neurons in the hidden layer which calcualate the output based on a **distance** in lieu of regular weighted sum.

The hidden layer is a nonlinear transform and the output layer is a simple linear combination.

![](Pasted%20image%2020250504214026.png)

Each input vector is completely transmitted to hidden neurons which are receptive fields. Those receptive fields are defined by a **center vector** $c_i$ and a nonlinear **receptive field function** $g$.
$$o(x)=g(d_i)=g(||x-c_i||)$$
> **Gaussian Receptive Field**
$$o(x)=\exp(-\frac{d_i^2}{2\sigma^2})=\exp(-\frac{||x-c_i||^2}{2\sigma^2})$$
> **Inverse Multi-quadratic Function**
$$o(x)=\frac{1}{\sqrt{d_i^2+\sigma^2}}=\frac{1}{\sqrt{||x-c_i||^2+\sigma^2}}$$

All the hidden layer neurons connect to the output layer, which contains regular weighted sum neuron **with no activation function**.
$$y=\sum_{i=1}^m w_io_i(x)+w_0=\sum_{i=1}^m w_ig(||x-c_i||+w_0)$$
---
## RBF Training 

+ **Parameters** - center vectors $c_i$, receptive field width $\sigma_i$, output weights and bias $w_i, w_0$

The training of a RBF network consists of two stages: receptive field determination and output weight estimation. 

### Receptive Field Determination

Choosing center vectors and receptive field widths is a significant step before starting the RBF training process since it decides the nonlinear transform of the network. There're several ways to do this, including: 

+ **Random Selection from training samples**
+ **Clustering** (K-means)
+ **Feature** ()



### Output Weight Estimation