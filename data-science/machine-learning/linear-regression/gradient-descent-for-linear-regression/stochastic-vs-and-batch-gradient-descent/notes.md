---
title: Stochastic Vs Batch Gradient Descent
topic: Gradient Descent for Linear Regression
slug: stochastic-vs-batch-gradient-descent
---

# Stochastic Vs Batch Gradient Descent

In stochastic gradient descent algorithm, we repeatedly run through the training set, and each time we encounter a training example, we update the parameters according to the gradient of the error with respect to that single training example only. Whereas batch gradient descent has to scan through the entire training set before taking a single step, which is a costly operation if $n$ is large. Stochastic gradient descent can start making progress right away, and continues to make progress with each example it looks at. 

Often, stochastic gradient gets close to the optimal parameter $\theta$, much faster than the batch gradient descent. However, it may not converge to optimal parameter ever Or it might keep oscillating around the minimum of $J(\theta)$. But, for most of the practical uses the solution that is near to the minimum also serves as a good approximate to the true minimum. ) For these reasons, particularly when the training set is large, stochastic gradient descent is often preferred over batch gradient descent.

---
