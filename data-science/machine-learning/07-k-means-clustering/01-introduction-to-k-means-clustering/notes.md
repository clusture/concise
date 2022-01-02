---
title: Introduction to k-Means Clustering
topic: k-Means Clustering
slug: k-means-clustering-intro
---

# Introduction to k-Means Clustering

In clustering problems, we are given a training set with $\{x^1, x^2, \ldots, x^n\}$. Here, we are not given a labels for the training examples.

The goal is to find is the grouping of a set of data points in such a way that data points in the same group (called a cluster) are more similar (in some sense) to each other than to those in other groups (clusters).

The following diagram provides the overview of clustering problem: 

![Clustering](./images/clustering.jpg)

K-means is a centroid based clustering technique. In centroid-based clustering, each cluster is represented by a central vector, which is not necessarily a member of the data set.

When the number of clusters is fixed to $k$, $k$-means clustering gives a formal definition as an optimization problem: find the k cluster centers and assign the objects to the nearest cluster center, such that the squared distances from the cluster are minimized.

$k$-means algorithm requires the number of clusters, $k$ to be specified in advance, which is considered to be one of the biggest drawbacks of these algorithms.

Furthermore, the algorithms prefer clusters of approximately similar size, as they will always assign an object to the nearest centroid. This often leads to incorrectly cut borders of clusters (which is not surprising since the algorithm optimizes cluster centers, not cluster borders).