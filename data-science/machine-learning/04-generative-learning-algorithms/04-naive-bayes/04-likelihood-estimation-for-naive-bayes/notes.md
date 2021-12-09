---
title: Likelihood Estimation for Naive Bayes
topic: Naive Bayes
slug: likelihood-estimation-naive-bayes
---

# Likelihood Estimation for Naive Bayes

We parameterized the model by $\phi_{i|y=1}, \phi_{i|y=0}, \text{and}\,\,\phi_y $. For a given training set $\{(x^i,y^i), i = 1,2, \ldots, m\}$, to estimate these parameters in order to compute $p(x|y)$ and $p(y)$, we use maximum likelihood estimation technique.

The first step in maximum likelihood estimation is to define the likelihood function. The likelihood function for naive bayes classifier is defined by :
$$\mathcal{L}(\phi_{i|y=1}, \phi_{i|y=0},\phi_y) = \prod_{i=1}^m p(x^i, y^i)$$

In the maximum likelihood estimation, the optimization problem is given by :
$${\underset {\phi_{i|y=1},\, \phi_{i|y=0},\,\phi_y}{\operatorname {max}}} \mathcal{L}(\phi_{i|y=1}, \phi_{i|y=0},\phi_y)$$

How to solve and find the optimal solution for the above optimization problem ?