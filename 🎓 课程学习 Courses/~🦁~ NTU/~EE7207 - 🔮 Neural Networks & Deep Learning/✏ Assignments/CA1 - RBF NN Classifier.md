
> [!QUESTION] Radial Basis Function Classifier
> Given a two-class pattern classification problem, whose training data is in the file data_train, and the label is in the file label_train, and the testing data is in data_test (50 samples, no label is provided)
> 1. Train a Gaussian RBF neural network classifier: describe how you determine the number of neurons in the input, hidden and output layer, and how you determine the width of Gaussian basis function, and what functions in the toolbox you use to train the network.
> 2. Predict the class label of the test data using the classifier trained

I choose PyTorch for this task because it's the de facto standard in the academia.
### I - Hyperparameters

#### Number of Hidden Neurons

The number of hidden neurons determine the nonlinear mapping output dimension of the hidden layer. It's usually decided by the square root of the number of training sample.
$$m=\sqrt{n_x}$$
Here I choose the hidden neuron number to be 20, which is slightly larger than square root of the number of training sample.

#### Initial Gaussian Width

The initial Gaussian function width $\sigma$ is usually calculated by the following formula in which $d_\max$ is the distance between the chosen vector and the farther center vector and $m$ is the number of vectors 
$$\sigma=\frac{d_\max}{\sqrt{2m}}$$
#### Gaussian Center Vectors

The Gaussian Center Vectors of the neurons are set using the K-means clusting algorithm. The number of clusters is the number of hidden neurons

```python
kmeans = KMeans(n_clusters=self.num_centers, random_state=0).fit(x_raw_data)
self.centers = nn.Parameter(torch.tensor(kmeans.cluster_centers_))
```

#### Input and Output Dimension

The input and output dimensions are set to 33 and 2 respective. The input dimension is the same as a sample's dimension and the output dimension is the number of label classes.

```python
input_dim = 33
output_dim = 2
```

#### Summary

| Hyperparameters                 | Value | Reason                  |
| ------------------------------- | ----- | ----------------------- |
| Input Dimension                 | 33    | sample dimension is 33  |
| Output Dimension                | 2     | 2 classes               |
| Hidden Layer Dimension          | 20    | determined by data size |
| Initial Gaussian Width $\sigma$ | /     | determined by distance  |
| Learning Rate $\eta$            | 0.01  | should be small         |

### II - Prediction

Here's my prediction

```python
myPrediction = [-1, 1, 1, -1, 1, 1, -1, 1, -1, -1, -1, 1, -1, -1, -1, -1, -1, 1, 1, -1, 1, 1, 1, -1, -1, 1, -1, 1, -1, 1, -1, 1, -1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]
```

### III - Source Code

```python
"""RBF Neural Network for classification"""

import numpy as np
import torch
import torch.nn as nn
import torch.optim as optim
from scipy.io import loadmat
from sklearn.cluster import KMeans
import numpy as np

class RBF(nn.Module):
    def __init__(self, input_dim, num_centers, output_dim, sigma):
        super(RBF, self).__init__()
        self.num_centers = num_centers
        self.centers = nn.Parameter(torch.randn(num_centers, input_dim))
        self.beta = nn.Parameter(torch.ones(num_centers) * (1/(2*sigma**2)))
        self.linear = nn.Linear(num_centers, output_dim)
    
    # Initialize RBF centers using KMeans
    def centers_init(self, x_raw_data):
        kmeans = KMeans(n_clusters=self.num_centers, random_state=0).fit(x_raw_data)
        self.centers = nn.Parameter(torch.tensor(kmeans.cluster_centers_))
        
    # Gaussian RBF function
    def gaussian_rbf(self, x):
        x = x.unsqueeze(0).expand(self.num_centers, -1)
        # print(x.size()) # Debugging
        # print(self.centers.size()) # Debugging
        distances = torch.sum((x - self.centers) ** 2, dim=1)
        return torch.exp(-self.beta * distances)

    def forward(self, x):
        phi = self.gaussian_rbf(x).to(torch.float32)
        # print(phi) # Debugging
        return self.linear(phi)

# Hyperparameters
input_dim = 33
num_centers = 20  # Adjust based on data complexity
output_dim = 2
learning_rate = 0.01
sigma = 1.0
epochs = 100
evaluation_split = 201 # Decide where to split the data for evaluation

# Load the .mat file
x_raw_data = loadmat("data_train.mat")["data_train"]
y_raw_data = loadmat("label_train.mat")["label_train"]
y_data = torch.tensor(y_raw_data, dtype=torch.int64)
y_data = torch.where(y_data < 0, 0, y_data)
y_data = torch.nn.functional.one_hot(y_data, num_classes=output_dim).squeeze().to(torch.float32)
x_data = torch.tensor(x_raw_data, dtype=torch.float32)

# Create training data
x_train = x_data[:evaluation_split]
y_train = y_data[:evaluation_split]

# Create evaluation data
x_eval = x_data[evaluation_split:]
y_eval = y_data[evaluation_split:]

# Initialize model
model = RBF(input_dim, num_centers, output_dim, sigma)
model.centers_init(x_raw_data)
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=learning_rate)

# print(x.size()) # Debugging
# print(y.size()) # Debugging

# Training loop
for epoch in range(epochs):
    optimizer.zero_grad()
   
    for i in range(x_train.size(0)):
        # print(i) # Debugging
        outputs = model(x_train[i])
        loss = criterion(outputs, y_train[i])
        loss.backward()
        # Update weights every 8 samples
        if i % 8 == 0 or i == x_train.size(0) - 1:
            optimizer.step()
            optimizer.zero_grad()
            
    if (epoch + 1) % 10 == 0:
        print(f"Epoch [{epoch+1}/{epochs}], Loss: {loss.item():.4f}")

print("Training complete!")

# Evaluate the model
correct_cnt = 0
for i in range(x_eval.size(0)):
    outputs = model(x_eval[i])
    if torch.argmax(outputs) == torch.argmax(y_eval[i]):
        print("\033[32mCorrect!\033[0m")
        correct_cnt += 1
    else:
        print("\033[31mIncorrect!\033[0m")

print("Accuracy: ", correct_cnt / x_eval.size(0))

# Test the model

# Load the test data
x_test = loadmat("data_test.mat")["data_test"]
x_test = torch.tensor(x_test, dtype=torch.float32)

# Predict the test data
y_predict = []
for i in range(x_test.size(0)):
    outputs = model(x_test[i])
    y_predict.append(-1 if torch.argmax(outputs) == 0 else 1)
    
print(y_predict)
```


---
## Files

![[65460837.pdf]]

![[data_train.mat]]

![[label_train.mat]]

![[data_test.mat]]