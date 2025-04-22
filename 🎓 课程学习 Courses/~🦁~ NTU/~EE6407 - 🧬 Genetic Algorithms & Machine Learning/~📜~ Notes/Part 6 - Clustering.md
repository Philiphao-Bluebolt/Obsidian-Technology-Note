+ **Goal** - Discover hidden grouping patterns in the dataset
+ **Type** - Unsupervised Learning

Clustering is one of the two topics of unsupervised learning (another is association analysis). It can discover clusters, the groups of nearby samples, without any former knowledege or label.

+ **Similarity Measurement** (Distance) 
	+ [Minkowski Distance](#Minkowski%20Distance)
	+ [Manalanobis Distance](#Manalanobis%20Distance)
	+ [K-Nearest Neighbours (KNN)](#K-Nearest%20Neighbours%20(KNN))
+ **Algorithms**
	+ [Centroids-based Clustering](#Centroids-based%20Clustering)
		+ [K-means](#K-means)
	+ [Hierarchical Clustering](#Hierarchical%20Clustering)
		+ [Agglomerative Algorithm](#Agglomerative%20Algorithm)
		+ [Division Algorithm](#Division%20Algorithm)
	+ [Distribution-based Clustering](#Distribution-based%20Clustering)
		+ [Gaussian Mixture Model (GMM) Clustering](#Gaussian%20Mixture%20Model%20(GMM)%20Clustering)
	+ [Density-based Clustering](#Density-based%20Clustering)
		+ [DBSCAN](#DBSCAN)
+ **Evalution**
	+ [Silhouette Coefficient](#Silhouette%20Coefficient)
	+ [Dunn Index](#Dunn%20Index)
	+ [Davies-Bouldin Index](#Davies-Bouldin%20Index)
	+ [Calinski-Harabasz Index](#Calinski-Harabasz%20Index)
	+ [Rand Index](#Rand%20Index)

---
## Minkowski Distance

+ **Goal** - Define the distance between a sample vector and a probability distribution

Minkowski Distance is a generalized form of Euclidean Distance and Manhattan Distance. Assume that $x,y$ are two sample vectors with dimension of $N$ and $x_i,y_i$ are the $i$ element of the vectors.

+ **Minkowski Distance**
$$d(x,y)=(\sum_{i=1}^\mathrm{N} |x_i-y_i|^q)^{\frac{1}{q}}$$
+ **Manhattan Distance** ($q=1$)
$$d(x,y)=\sum_{i=1}^\mathrm{N} |x_i-y_i|$$
+ **Euclidean Distance** ($q=2$)
$$d(x,y)=\sqrt{\sum_{i=1}^\mathrm{N} (x_i-y_i)^2}=||x-y||_2$$

---
## Manalanobis Distance

+ **Goal** - Define the distance between a sample vector and a probability distribution (or cluster)

Assume that the data dimension is $N$. $x$ is the sample point and $p$ is the distribution with mean $\mu$ and covariance matrix $\Sigma$

+ **Manalanobis Distance**
$$d(x, p)=\sqrt{(x-\mu)^T \Sigma^{-1}(x-\mu)}$$

When the data dimension $N=1$, the equation can be simplified into
$$d(x,p)=\frac{||x-\mu||_2}{\Sigma}$$

---
## K-Nearest Neighbours (KNN)

+ **Goal** - Define the distance between a sample and a cluster or between two clusters






---
## Centroids-based Clustering

+ **Pros** - Simple
+ **Cons** - Cluster number needed, Poor on arbitrary-shaped and noisy clusters

Centroids-based methods divide the data into non-hierarchical groups by assigning the samples into clusters represented by centroids vectors. They're the most simpliest types of clustering algorithms but can not handle data with arbitrary-shaped and noisy cluster.

### K-means

+ **Hyperparameters** - Cluster Number $k$

K-means clustering is based on the process of moving centroids. In every steps, all the sample points are assigned to the nearest centroid and thus, form clusters. After assignment, new centroids are updated as the mean vector of each cluster.

> [!NOTE] K-means Algorithms
> + Randomly generate $k$ inital centroids
> + Repeat until the centroids are stable
> 	1. Assign every sample to the nearest centroid
> 	2. Update the centroids as the cluster mean

It's crucial to properly set the number of clusters $k$ for the best performance. Intuitively, preferable clustering results should have all their sample points near corresponding centroids. This idea leads into the WSCC criterion.

The meaning of WSCC is simply the sum of Euclidean distances between all sample and their cluster centroids.

+ **WSCC** (Within Cluster Sum of Squares)
$$\mathrm{WSCC}=\sum_{i=1}^k(\sum_{x_j\in{D_i}}||x_j-m_i||_2)$$
+ **Elbow Method** - Choose the number of clusters $k$ at the **inflection point** (elbow point) of WCSS-$k$ function. 


![](Pasted%20image%2020250415115219.png)

---
## Hierarchical Clustering

+ **Pros** - No need to decide cluster numbers, 
+ **Cons** - 

Hierarchical clustering is a type of tree-based method which represents the distances between data points as a tree. The clusters can be derived from the branches of the tree.

Two controdictrary concept of hierarchical clustering are **Agglomerative** (Bottom-up) and **Divisive** (Top-down)

### Agglomerative Algorithm

+ **Predefinition** - Similarity Measurement, Clustering Threshold (a distance)

Each sample is a sub-cluster at the beginning of agglomerative clustering. In every step, the two elements (samples or clusters) with the smallest distance are combined into a larger cluster. 

> [!NOTE] Agglomerative Algorithms
> + Repeat until all the samples are combined into the same cluster
> 	1. List all the distances between every two elements (samples or clusters)
> 	2. Combine the two samples with the smallest distance into a larger cluster
> 	3. The newly-formed cluster will join the next match as a whole
> + Choose an Euclidean distance as the clustering threshold and derived the clusters

![](Pasted%20image%2020250415122953.png)
The algorithm usually used one of the following forms as the similarity measurement between two clusters or a sample and a cluster:

+ **Simple Linkage** (Nearest Pair) - the distance between two nearest sample pair
$$d(D_x,D_y)=\min_{x_i\in D_x,y_j\in D_y} ||x_i-y_j||_2$$

+ **Complete Linkage** (Farthest Pair) - the distance between two farthest sample pair
$$d(D_x,D_y)=\max_{x_i\in D_x,y_j\in D_y} ||x_i-y_j||_2$$

+ **Centroid Linkage** (Centroid Pair) - the distance between two centroids
$$d(D_x, D_y)=||m_x - m_y||_2$$

+ **Average Linkage** - the average distance of all the possible pairs 
$$d(D_x, D_y)=\frac{1}{n}\sum_{x_i\in D_x,y_j\in D_y}||x_i-y_j||_2$$

### Division Algorithm

Division Algorithm is the dual form of Agglomerative Algorithm. All the samples are included into a super cluster at the beginning and the pair of elements with largest distance is seperated first.

---
## Distribution-based Clustering

+ **Pros** - 
+ **Cons** - Cluster number needed

Distribution-based methods attempt to represent the whole dataset as the mixture of several probability distributions and assign the samples to the nearest distributions. 

### Gaussian Mixture Model (GMM) Clustering

+ **Hyperparameters** - Cluster Number $k$

The GMM Clustering makes use of the **Expection-Maximization (EM) Algorithm**. A number of $k$
Gaussian distributions are used to represent the whole dataset and each sample is assigned to the nearest distribution center.

> [!NOTE] GMM Clustering Algorithm
> + Randomly Initiate the mean $\mu_i$, covariance $\Sigma_i$ and weight $\alpha_i$ of $k$ Gaussian distribution
> + Run the EM algorithm
> + Assign each sample to the nearest distribution centers.

![](Pasted%20image%2020250415135055.png)


---
## Density-based Clustering

+ **Pros** - Work well on arbitrary-shaped and noisy dataset, No need to decide cluster numbers 
+ **Cons** - Poor on varying-density clusters, Non-deterministic, Neighbourhood Radius $\varepsilon$ sensative on high-dim dataset

Density-based Clustering creates clusters by combining all the neighbour samples.

### DBSCAN

+ **Hyperparameters** - Density Threshold $M$,  Neighbourhood Radius $\varepsilon$

DBSCAN (Density-based Spatial Clustering of Applications with Noise) operates under the following definitions. 

Firstly, two points are considered **neighbours** if their distance is smaller than the Neighbourhood Radius $\varepsilon$

+ Point Types
	+ **Core Point** - there exist more than $M$ neighbours (include itself) around it
	+ **Border Point** - not a core point but is the neighbour of a core point
	+ **Noise Point** - any points else
+ Point Relationships
	+ **Directly Density-Reachable** - a core point $q$ can reach its neightbour border point $p$  
	+ **Density-Reachable** - a core point $q$ can reach a border point $p$ through a series of core points  
	+ **Density-Connected** - two points are connected by a series of core point

> [!NOTE] DBSCAN Algorithm
> + Repeat until all points are visited
> 	1. Randomly choose a unvisited point
> 	2. Recursively find all the **density-connected** points of the chosen point
> 	3. Assign all the connected points to a cluster and mark them as visited
> + All the isolated points (each forms a cluster with only itself) are considered noise

The selection of parameters is based on experience

+ $M$ - usually $M=2N$ ($N$ is the dataset dimension), larger value should be used for noisy data
+ $\varepsilon$ - using elbow method on the $k$ - $\varepsilon$ function ($k=M-1$)

---
## Silhouette Coefficient




---
## Dunn Index



---
## Davies-Bouldin Index



---
## Calinski-Harabasz Index



---
## Rand Index