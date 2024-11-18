[[#Softmax Loss Calculation]]
[[#CNN Classical Computation]]


---
## Softmax Loss Calculation 

The output score of a linear image classifier receiving a cat iamge as input is shown in the table, calculate the softmax loss of the output result

| Categories | Output Score $z$ | Groundtruth Score $y$ |
| :--------: | :--------------: | :-------------------: |
|  airplane  |       0.7        |           0           |
| automobile |       0.1        |           0           |
|    bird    |       1.6        |           0           |
|    cat     |       2.2        |           1           |
|    deer    |       0.3        |           0           |

Firstly, we use the softmax function to calculate the generalized possibility for the output score of each category.
$$p_j=\frac{e^{z_j}}{\sum_{k=1}^5 e^{z_k}}$$

| Categories | Output Score $z_j$ | Groundtruth Score $y_j$ | Softmax generalized possibility $p_j$ |
| :--------: | :----------------: | :---------------------: | :-----------------------------------: |
|  airplane  |        0.7         |            0            |                                       |
| automobile |        0.1         |            0            |                                       |
|    bird    |        1.6         |            0            |                                       |
|    cat     |        2.2         |            1            |                                       |
|    deer    |        0.3         |            0            |                                       |

Then just use the cross-entropy formula to calculate the final result
$$L=-\sum_{j=1}^5 y_j \ln p_j=$$


---
## CNN Feature Extraction

A grayscale image $A$ passes through a convolution layer, a activation layer and a max pooling layer. 
$$A=\begin{bmatrix}4&0&1\\4&0&2\\0&2&2\end{bmatrix}$$
+ Convolution layer - The convolution kernel is given by $F$. The stride is 2 both vertically and horizontally. The amount of zero padding is 1  
$$F=\begin{bmatrix}1&0&-1\\2&0&-2\\1&0&-1\end{bmatrix}$$
+ Activation layer - Signmoid function
$$\sigma(x)=\frac{1}{1+e^{-x}}$$
+ Pooling layer - Max pooling with 2x2 kernel and stride of 2

**Queations:**
1. Find the output of each layer
2. Discuss the effect of $F$ when applied to the image
3. Find the number of trainable parameters of the new convolution layer after changing the input image to a 100x100 RGB image and the channel number of output maps to 6 
	+ No bias is used
	+ Kernel size remain 3x3

#### (1)

The output of the convolution layer is a 2x2 image
$$A'=\begin{bmatrix}0&0\\-4 &4\end{bmatrix}$$
The output after activated
$$A''=\begin{bmatrix}0&0\\0.018 & 0.982\end{bmatrix}$$
The output after pooling
$$A'''=0.982$$
#### (2)

The convolution kernel actually computes the horizontal gradient.

#### (3)

For the convolution layer, the only trainable part are the convolution kernels. Since the input image has 3 channels now, 3 different kernels can be used in the convolution process 

Then the output has 6 channel, meaning that the input image will be mapped 6 times

$$3\times 3\times 3\times 6=162$$

---
## CNN FC & Softmax

A input vector $x$ passes through a Fully Connected Layer of CNN with the following weight matrix and bias
$$x=\begin{bmatrix}0.3\\0\\0.2\\0.1\end{bmatrix}\quad\quad\quad W=\begin{bmatrix}0&3&7&8\\1&8&0&0\\0&8&1&0\end{bmatrix}\quad\quad\quad b=\begin{bmatrix}-1\\1\\2\end{bmatrix}$$
**Queations:**
1. Find the FC output
2. Find the softmax output

#### (1)

The output of FC is just a simple linear combination
$$y=Wx+b=\begin{bmatrix}0&3&7&8\\1&8&0&0\\0&8&1&0\end{bmatrix}\begin{bmatrix}0.3\\0\\0.2\\0.1\end{bmatrix}+\begin{bmatrix}-1\\1\\2\end{bmatrix}=\begin{bmatrix}1.2\\1.3\\2.2\end{bmatrix}$$
#### (2)

The softmax function is applied to the output score
$$$$


---
## LSTM 



---
## Model Comparison