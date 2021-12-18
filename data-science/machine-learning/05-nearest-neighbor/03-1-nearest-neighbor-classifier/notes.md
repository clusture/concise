---
title: 1-Nearest Neighbor Classifier
topic: Nearest Neighbors
slug: 1-nearest-neighbor-classifier
---

# 1-Nearest Neighbor Classifier

Let $\{(x^i,y^i): i=1,\ldots,m\}$ be the training set. The goal of the classifier is to assign the class label for a new/query data point. Let $x^q$ be the feature vector corresponding to the the query data point.

The 1-nearest neighbor classifier takes the following steps :
1. Pick the distance measure you want to use for finding the similarity
2. Calculate the distance between the query point $x^q$ and the rest of points in the training set
3. Find the closest point to the query point $x^q$. Closest point is called the nearest neighbor
4. Assign the class label of the query point $x^q$ as for the class label of the nearest neighbor

1-nearest neighbor is often called as 1-NN. 1-NN is the simplest of all the nearest neighbor classifiers.
