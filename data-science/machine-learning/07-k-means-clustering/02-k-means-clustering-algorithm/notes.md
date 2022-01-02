---
title: k-Means Clustering Algorithm
topic: k-Means Clustering
slug: k-means-clustering-algo
---

# k-Means Clustering Algorithm

The following are the steps of k-means clustering algorithm:

1. Initialize the centroids $\{\mu^1, \mu^2, \ldots, \mu^n\}$ to be randomly selected from the training set. Here, $\mu^i \in \mathbb{R}^d$.
2. Repeat
    - Assign for each training example $x^i$, the nearest centroid. This is given by solving the following :
        $$
        \begin{aligned}
        c^i = \argmin_{k} & ||x^i - \mu^k||^2 
        \end{aligned}
        $$

    - Update the centroids $\{\mu^1, \mu^2, \ldots, \mu^n\}$ to be the mean of the assigned training examples. The new centroid is calculated as:
        $$
        \begin{aligned}
        \mu^i = \frac{\sum_{j=1}^n \mathbb{1}\{c^j = i\} x^j}{\sum_{j=1}^n \mathbb{1}\{c^j = i\}} 
        \end{aligned}
        $$

3. Stop when the centroids do not change.


In the algorithm above, $k$ (a parameter of the algorithm) is the number of clusters we want to find. And the cluster centroids $\mu^j$ represent our current guesses for the positions of the centers of the clusters. 
