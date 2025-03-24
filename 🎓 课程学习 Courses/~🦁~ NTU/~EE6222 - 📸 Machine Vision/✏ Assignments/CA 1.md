### Part I - Experiment Report

High dimension datasets are common in the domain of machine learning and neural networks. Although they're rich in information, the high-dimensionality greatly reduces the speed of model training and bring challenges to analysis of the data. Fortunately, several methods including PCA (Principal Component Analysis) and LDA (Linear Discriminant Analysis) have been invented to reduce features from a dataset. The following experiment will compare the performance of these two methods.

The Fashion MNIST dataset is chosen as the testing dataset of the experiment for its high-dimensionality (28x28=784). It's a dataset of 70000 images in 10 classes of clothings in which 60000 images are used for training and 10000 for testing.

![](Pasted%20image%2020250323213224.png)

The logic of the program can be broke into three parts. 

1. **Data Input** - images data are read from the `.csv` dataset and split into training and testing set.
2. **Dimension Reduction** - PCA and LDA algorithms are applied to the generalized data respectively and reduced the dimension in different scales. 
3. **Classification** - logistic regression and kNN are used as classifiers for the data respectively.

The classification accuracy is ploted as below. The LDA can only reduced the number dimension into a smaller number than the number of classes so the plot doesn't cover the LDA accuracy data with dimension more than 10.
![](Figure_1%201.png)

Some conclusions can be drawn from the experimental results. 

1. **Data Dimension and Accuracy** - When the data dimension is reduced, the accuracy of classification rises and then falls. This phenomenon is likely a complex effect of dimension reduction. The reduction of dimension from 784 to 200 mitigates the overfit and slightly increases the accuracy. However, when the reduction is aggressive, the severe loss of information graduately decreases the accuracy.
2. **KNN vs LR** - When the data dimension is large, KNN has better performance than Linear Regression.
3. **LDA vs PCA** - When the data dimension is reduced to a small number, the LDA algorithm performs better than the PCA. 


### Part II - Source Code

```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
from sklearn.decomposition import PCA
from sklearn.neighbors import KNeighborsClassifier
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis as LDA
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score
from sklearn.preprocessing import StandardScaler

# Load Fashion-MNIST dataset
test_data = pd.read_csv("fashion_mnist/fashion-mnist_test.csv")
train_data = pd.read_csv("fashion_mnist/fashion-mnist_train.csv")

# Seperate label and features
X_train = train_data.values[:,1:]
X_test = test_data.values[:,1:]
y_train = train_data.values[:,0]
y_test = test_data.values[:,0]

# Normalize data (scale to mean=0, variance=1)
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
print(X_train.shape)

dim_reduce_to = [1, 2, 5, 10, 20, 50, 100, 200, 500]
accuracy_pca = []
accuracy_lda = []
accuracy_pca_knn = []
accuracy_lda_knn = []

for dim_reduced in dim_reduce_to:

    # PCA dimension reduction
    pca = PCA(n_components=dim_reduced)
    X_train_pca = pca.fit_transform(X_train)
    X_test_pca = pca.transform(X_test)

    # Train classifier on PCA-transformed data
    clf_pca = LogisticRegression(max_iter=1000)
    clf_pca.fit(X_train_pca, y_train)
    y_pred_pca = clf_pca.predict(X_test_pca)
    accuracy_pca.append(accuracy_score(y_test, y_pred_pca))

    # Train the KNN classifier on PCA-transformed data
    knn_pca = KNeighborsClassifier(n_neighbors=3)
    knn_pca.fit(X_train_pca, y_train)
    y_pred_pca = knn_pca.predict(X_test_pca)
    accuracy_pca_knn.append(accuracy_score(y_test, y_pred_pca))

    if dim_reduced < 9:

        # LDA dimension reduction
        lda = LDA(n_components=dim_reduced)
        X_train_lda = lda.fit_transform(X_train, y_train)
        X_test_lda = lda.transform(X_test)

        # Train classifier on LDA-transformed data
        clf_lda = LogisticRegression(max_iter=1000)
        clf_lda.fit(X_train_lda, y_train)
        y_pred_lda = clf_lda.predict(X_test_lda)
        accuracy_lda.append(accuracy_score(y_test, y_pred_lda))

        # Train the KNN classifier on PCA-transformed data
        knn_lda = KNeighborsClassifier(n_neighbors=3)
        knn_lda.fit(X_train_lda, y_train)
        y_pred_lda = knn_lda.predict(X_test_lda)
        accuracy_lda_knn.append(accuracy_score(y_test, y_pred_lda))

    print(f"Finish Dimension Reduction to {dim_reduced}")

# Print results
print(f"PCA Accuracy: {accuracy_pca}")
print(f"LDA Accuracy: {accuracy_lda}")
print(f"PCA Accuracy kNN: {accuracy_pca_knn}")
print(f"LDA Accuracy kNN: {accuracy_lda_knn}")

# Plot PCA explained variance
plt.figure(figsize=(8, 5))
plt.plot(dim_reduce_to, accuracy_pca, label="PCA LR", marker=".")
plt.plot(dim_reduce_to[0:3], accuracy_lda, label="LDA LR", marker="*")
plt.plot(dim_reduce_to, accuracy_pca_knn, label="PCA KNN", marker="x")
plt.plot(dim_reduce_to[0:3], accuracy_lda_knn, label="LDA KNN", marker="o")
plt.xlabel("Number of Dimensions")
plt.ylabel("Accuracy")
plt.title("PCA and LDA Accuracy Comparison")
plt.xscale('log')
plt.grid()
plt.legend()
plt.show()
```