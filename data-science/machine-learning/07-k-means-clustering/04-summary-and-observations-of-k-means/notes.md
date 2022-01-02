---
title: Summary and Observations of k-Means Algorithm
topic: k-Means Clustering
slug: summary-observations-k-means-algo
---

# Summary and Observations of k-Means Algorithm

$k$-means is one of the simplest algorithms in unsupervised machine learning. We saw one of the unsupervised learning problems known as clustering and how $k$-means algorithm finds $k$ clusters for a given dataset.

$k$-means can be susceptible to local optima. It may not find the best clusters for the dataset theoretically. However, very often k-means will work fine and come up with very good clustering despite this in practice. One simple hack often being employed to avoid getting stuck in bad local minima, to run k-means many times with random initializations.