Two modules from the Sci-Kit Learn Library have been implemented here from scratch:

1. t-SNE or t-Distributed Stochastic Neighbour Embedding
2.  K-Means Clustering

## t-SNE or t-Distributed Stochastic Neighbour Embedding

t-SNE (t-Distributed Stochastic Neighbor Embedding) is a machine learning algorithm used for dimensionality reduction and visualization. It is effective in exploring and visualizing high-dimensional datasets by mapping them to a lower-dimensional space (usually 2D or 3D). 

t-SNE involves two main steps:

1. **Measure Pairwise Similarities in High Dimensions:**
   
 - For each pair of data points in the high-dimensional space, t-SNE calculates a probability of similarity where points closer together have higher probabilities. This is modeled using a Gaussian distribution.

2. **Measure Pairwise Similarities in Low Dimensions:**
   
 - In the low-dimensional space, t-SNE attempts to recreate the similarity probabilities from the high-dimensional space. This is modeled using a t-distribution, which has heavier tails than a Gaussian. This choice helps spread out points and avoid overcrowding.

3. **Minimize the Difference Between the Two Similarities:**
   
 - t-SNE minimizes the difference (using KL divergence) between the high-dimensional and low-dimensional similarity distributions. It uses gradient descent to iteratively update the positions of points in the low-dimensional space.

The model has been tested on the Iris Dataset, which contains samples of flowers, each described by four features:
Sepal length
Sepal width
Petal length
Petal width

The results of the model designed from scratch are compared with the built in t-SNE module from the sci-kit learn library.



## K-Means Clustering

K-Means Clustering is anunsupervised machine learning algorithm for grouping data into clusters based on their features. It works by iteratively partitioning the dataset into k groups, where k is specified by the user.

The K-Means algorithm follows these steps:

1. **Initialization:**

 - Randomly place k cluster centroids in the feature space. k is the number of clusters you specify.

2. **Assignment:**

 - Each data point is assigned to the nearest centroid based on a distance metric (commonly Euclidean distance).
Update Centroids:
 - The centroids are updated to the mean of the points assigned to them.
   
3. **Repeat:**

 - Steps 2 and 3 are repeated until the centroids stabilize (i.e., they don’t change significantly) or a maximum number of iterations is reached.

### Evaluating the clusters:

- The clustering is evaluated by Within-Cluster Sum of Squares (WCSS). WCSS calculates the sum of squared distances between each data point and the centroid of its assigned cluster. The goal is to minimize this value, which indicates that the points are tightly grouped around their centroids. 

- An issue with K-Means lies in the random initialisation of centroids. If the centroid are not initialised well, no matter how many iterations of K-Means take place, we will get a high WCSS. This problem is solved by initialising the centroids multiple times and taking the final cluster with the lowest WCSS. The number of times the centroids are initialised are passed in by the user as a hyperparameter.



