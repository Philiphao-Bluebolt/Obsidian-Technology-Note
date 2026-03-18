+ **Goal** - obtain useful features from the images
+ ****

Features are predefined format of data that can be generated and extracted from an image. For example, all of the properties of an image shown below can be considered a feature.

+ The image itself ($m\times n$ matrix)
+ Its histogram ($L$-dim vector)
+ Its fourier transform ($m\times n$ matrix)
+ The average grey level of a certain subregion

The selection of **feature representative** is determined by the specific **task**. After this, features are obtained with three stages

+ **Generation** - obtain feature from the image
+ **Selection** - select the most relevant feature
+ **Extraction** - reduce the dimension of feature for ease of processing

+ [[#Feature Generation]]
	+ [[#Harr-like Features]]
+ [[#Feature Selection]]
	+ [[#Adaboost]]
	+ [[#Attentional Cascade Classifier]]
+ [[#Feature Extraction]]
	+ [[#Principal Component Analysis]]
	+ [[#Linear Discriminant Analysis]]

---
## Feature Generation

+ **Goal** - obtain the desired feature representative from the image

### Harr-like Features

Harr-like features are generated using a rectangle window with two regions. The feature representative is defined as the **difference** of pixel grey level sum in **two regions**.

The calculation of Harr-like feature is based on the integral image $f_i(x,y)$ of $f(x,y)$
$$f_i(x,y)=\sum^y_{j=0}\sum^x_{i=0}f(x,y)$$
The pixel grey level sum of a rectangle region $f_s$ can be easily calculated through
$$f_s(x_1<x<x_2,y_1<y<y_2)=f_i(x_2,y_2)+f_i(x_1,y_1)-f_i(x_1,y_2)-f_i(x_2,y_1)$$
![[Pasted image 20250225223554.png]]


---
## Feature Selection

+ **Goal** - 
+ **Methods** - Adaboost, Attentional Cascade Classifier

### Adaboost


### Attentional Cascade Classifier




---
## Feature Extraction

+ **Goal** - reduce the size or dimension of features for further analysis
+ **Methods** - PCA, LDA

Features extraction reduces the dimension of feature to make the computing less time-consuming. The

### Principal Component Analysis





### Linear Discriminant Analysis

