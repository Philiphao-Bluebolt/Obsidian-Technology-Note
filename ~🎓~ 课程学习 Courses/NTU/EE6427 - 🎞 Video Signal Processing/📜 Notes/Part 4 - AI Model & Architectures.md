+ **Topics** - Linear Classifier, CNN, RNN, LSTM, Transformer  

AI Model are rising a revolution in the study of image and video processing. 

+ DNN (Deep Neural Network) Basis
	+ [[#Basic DNN structures]]
		+ [[#Perceptron]]
		+ [[#Multilayer Perceptron]]
	+ [[#Loss Function]]
+ CNN (Convolutional Neural Network) --> Image Processing
	+ [[#CNN Classical Architecture]]
		+ [[#Convolution]]
		+ [[#Activation]]
		+ [[#Pooling]]
	+ [[#CNN Training]]
+ RNN (Recurrent Neural Network) --> Sequence Processing
	+ [[#RNN Classical Architecture]]
+ LSTM (Long Short-term Memory) --> Sequence Processing
	+ [[#LSTM Classical Architecture]]
+ Transformer
	+ [[#Attention Mechanism]]


---
## Basic DNN structures

The concept of DNN is mainly inspired by how human neural system work. DNN is consists of perceptron connecting each other, which resemble the structure of connecting neurons in actual neural system.

## Perceptron

Perceptrons are the unit elements of neural networks. They're inspired by the structure of neurons in human brains.

+ Weights / Parameters - **Weight** matrices are the most significant part of the perceptron as they determine the output behavior of the perceptron. When training a DNN, weights matrices are changed, so they're also called **parameters**
![[Pasted image 20241022162827.png]]
## Multilayer Perceptron

When enormous perceptors are connected together, they form a neural network. Since the number of parameters (weights) in a neural network is much larger than in a single perceptron, the network is capable of capturing more patterns.

The simplest neural network is the feed-forward network. It contains of different layers of perceptrons and has no loop or backward path.

![[Pasted image 20241023140001.png]]

---
## Loss Function

+ **Goal** - Measure the distance between ground truth and network output

Loss Function are classified into two categories corresponding to two types of common AI problems.

For **regression** problems, the loss function can take the following forms, being either squared or averaged.

+ Square Loss
$$SE=\sum_i (y_i-f(x_i))^2$$
+ Mean Square Error
$$MSE=\frac{1}{N}\sum_i (y_i-f(x_i))^2$$
+ Mean Absolute Error
$$MAE=\frac{1}{N}\sum_i |y_i-f(x_i)|$$
For classification problems, the softmax loss is frequently used.
$$z_j=f(x_j)$$
$$p_j=\frac{e^{z_j}}{\sum_k e^{z_k}}$$
$$L=-\sum_j y_j \ln p_j$$
+ $j, k$ - index of a category
+ $z_j$ - output score of the jth category
+ $p_j$ - softmax normalized possibility for the jth category 

The result of loss function is used to determine which direction should the weights shift.


---
## Typical AI Models

#### Linear Classifier 






---
## CNN Classical Architecture 

 + **Feature** - Convolution Layer

Convolutional Neural Network features mask-convolution in some of the middle layers. It's mostly used for image processing. A typical CNN consists of the following layers or processing stages

+ Feature Extraction (Repeat multiple times)
	+ Convolution
	+ Activation (Non-linear mapping)
	+ Pooling (Sub-sampling)
+ Classification
	+ Full-connected Layer
	+ Softmax

### Convolution

Convolution operation of image is similar to convolution in signal processing. A mask is applied to the image, operating 

There're two pre-convolution process

+ **Padding** - Complementary of pixels around the original image
+ **Striding** - Distance of pixels the mask moves each time 


### Activation

The activation function is a element-wise non-linear function which is applied to the output image after each convolution. 

Here are some of the typical activation functions, Relu is the most popular among them. 



### Pooling

Pooling is the sub-sampling process following convolution and activation. Typical pooling mask includes max pooling and average pooling



---
## CNN Training




---
## RNN Classical Architecture

 + **Feature** - Hidden State $h$

The concept of RNN is comparable with the state space in control theory, both introduce state variables which keep memory of the past input.

$$\begin{cases}h_t=f_W(h_{t-1}, x_t)=\tanh(W_{hh}h_{t-1}+W_{xh}x_t)\\y_t=W_{hy}h_t\end{cases}$$



---
## LSTM Classical Architecture

+ **Feature** -  




---
## 


---
## Attention Mechanism

