# Project Summary: K-Means Clustering Implementation and Analysis

## 1. Introduction

This project focuses on understanding, implementing, and evaluating the K-Means clustering algorithm. K-Means is one of the most widely used unsupervised machine learning algorithms for partitioning datasets into groups based on similarity.

The project includes:
- A **from-scratch implementation** of K-Means using NumPy
- **Synthetic dataset generation** for controlled experimentation
- **Elbow method** analysis to determine the optimal number of clusters
- **Visual comparisons** between custom and scikit-learn implementations
- **Performance benchmarking** to evaluate efficiency and convergence behavior

This project is designed for educational and practical understanding of clustering algorithms.

---

## 2. Custom K-Means Algorithm

A complete K-Means algorithm was implemented manually without using any built-in clustering functions. The key steps involved are:

### 2.1 Initialization
- The algorithm begins by randomly selecting `k` data points from the dataset as the initial centroids.
- The random seed can be optionally set to ensure reproducible results.

### 2.2 Cluster Assignment
- For each data point, the Euclidean distance to each centroid is calculated.
- Each point is assigned to the cluster with the closest centroid.
- The **inertia**, defined as the sum of squared distances between points and their assigned centroid, is computed as a measure of cluster compactness.

### 2.3 Centroid Update
- For each cluster, the centroid is updated by taking the mean of all points assigned to that cluster.
- If a cluster receives no points, the centroid remains unchanged to avoid invalid operations.

### 2.4 Convergence Check
- The algorithm checks whether the centroids have moved less than a small tolerance value (`tol`).
- If centroid movement is below this threshold, the model is considered converged and training stops early.
- A maximum iteration limit prevents infinite loops.

### 2.5 Final Outputs
After training, the algorithm returns:
- Final centroid positions
- Cluster labels for each point
- Final inertia
- Number of iterations performed

---

## 3. Dataset Generation

A synthetic dataset was created specifically to test the behavior of the algorithm:
- **300 samples**
- **2 numerical features**
- **4 true underlying cluster centers**
- **Cluster standard deviation of 0.6**
- Generated using `sklearn.datasets.make_blobs`

This controlled dataset allows:
- Visual inspection of clustering performance
- Clear evaluation of centroid accuracy
- Comparison with true labels

A scatter plot shows well-separated clusters, making it easy to visualize the algorithm’s effectiveness.

---

## 4. Elbow Method Analysis

The elbow method helps determine the optimal value of `k` by:

1. Running K-Means for a range of cluster counts (e.g., `k = 1 to 10`)
2. Computing inertia for each value of `k`
3. Plotting inertia vs. the number of clusters

The “elbow point” on the graph indicates diminishing returns from increasing `k`.  
For the synthetic dataset, the elbow typically appears around **k = 4**, aligning with the true number of cluster centers.

---

## 5. Clustering Visualization

Visualization is crucial to understanding how well the algorithm performs.

### 5.1 True Labels Plot
- Colored scatter plot showing actual clusters from dataset generation.

### 5.2 Custom K-Means Result
- Original data colored by predicted cluster assignment
- Centroid positions highlighted

### 5.3 Comparison with scikit-learn KMeans
- scikit-learn often converges faster due to optimized C implementations
- Both methods produce similar cluster boundaries for this dataset

---

## 6. Performance Comparison

Comparisons were made between:
- **Custom K-Means implementation**
- **sklearn.cluster.KMeans**

### 6.1 Metrics Evaluated
- Total inertia
- Number of iterations
- Runtime performance
- Cluster boundary accuracy

### 6.2 Key Observations
- The custom implementation produces nearly identical clusters compared to scikit-learn.
- scikit-learn performs faster because:
  - It uses optimized vectorized operations in C
  - It offers advanced initialization methods like K-Means++

- The custom implementation is still efficient for small datasets and demonstrates the algorithm’s logic clearly.

---

## 7. Conclusion

This project provides a comprehensive exploration of the K-Means clustering algorithm. Key takeaways include:

- K-Means is simple and powerful for partitioning structured data.
- The manual implementation helps reveal the underlying geometric intuition of clustering.
- Synthetic datasets allow controlled evaluation and comparison.
- The elbow method is an effective tool for estimating the optimal number of clusters.
- While scikit-learn is more optimized, the custom implementation performs competitively on small datasets.

This project serves as a strong foundation for further exploration of:
- K-Means++
- Mini-batch K-Means
- High-dimensional clustering
- Real-world applications such as image segmentation and customer segmentation

