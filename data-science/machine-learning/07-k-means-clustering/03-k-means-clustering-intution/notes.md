---
title: k-Means Clustering Algorithm Intuition
topic: k-Means Clustering
slug: k-means-clustering-algo-intuition
---

# k-Means Clustering Algorithm Intuition

Let us understand the working of k-means clustering algorithm. The following diagram illustrates the algorithm in a step-by-step manner.

![K-Means](./images/k-means-algorithm.png)

In this diagram,
1. First, step $a$ shows training examples in green circles. These points did not contain any class labels.
2. The next step, step $b$ of $k$-means clustering algorithm shows the randomly assigned centroids in crosses. 
3. we assign each training example to the closest cluster centroid (shown by "painting" the training examples the same color as the cluster centroid to which is assigned in step $c$)
4. Once the points are assigned centroids, the centroids are reevaluated or moved based on the mean of the data points assigned to it. It is shown in the step $d$
5. Repeat the steps from 2 to 4 until the convergence.

We can see that, data points are grouped into clusters at the end of the $k$-means algorithm based on the similarity (here distance).