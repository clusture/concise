---
title: Filter Methods
topic: Learning Theory Topics
slug: filter-methods
---

# Filter Methods

Filter methods give heuristic and cheaper way of choosing the subset of features. The idea here is to compute some score $S(i)$ that measures, how informative each feature $f_i$ is to compute the class label $y$. Then, we simply pick the top $k$ features with largest scores $S(i)$. 

One possible choice of score would be to define $S(i)$ to be the correlation between $f_i$ and $y$, as measured on the training set. This results in choosing the features that are most common to choose $S(i)$ to be the mutual information MI($f_i,y$) between $f_i$ and $y$:
$$MI(f_i,y) = \sum_{x_i \in \{0,1\}} \sum_{y \in \{0,1\}} p(x_i, y)\,\, log \frac{p(x_i, y)}{p(x_i)\, p(y)}$$

Here, we assume that the feature $f_i$ and $y$ are binary valued. And the probabilities $p(x_i, y)$, $p(x_i)$ and $p(y)$ can be estimated empirically through their distributions in the training set.

Larger the $MI(f_i, y)$ value means, more informative or important that feature. If feature $f_i$ is less informative then $MI(f_i, y)$ or mutual information value will be less.

Now that we have scores corresponding to each feature giving how much informative that feature is, How to select the $k$ features from this ? We can employ cross-validation technique to select the $k$ features.