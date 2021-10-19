---
title: Logistic Regression Model
topic: Logistic Regression Model
slug: logistic-regression-model
---

# Logistic Regression Model

Let us recall the hypothesis function of logistic regression algorithm : $$\begin{aligned} h_{\theta}(x) &= g(\theta^{T}x) \\&= \frac{1}{1 + e^{\theta^T x}}\end{aligned}$$

We know that $h_{\theta}(x)$ is always bounded between 0 and 1 due to property of sigmoid function $g$. We are keeping the convention of letting $x_0 = 1$ so that $\theta^Tx = \theta_0 + \sum_{j=1}^d \theta_j x_j$.

There are still two questions left for which we need to find answer. One, for binary classification task, the algorithm need to output either $0$ or $1$. But, the output of logistic regression's hypothesis function is between $0$ and $1$. We will find the answer for it using the decision boundaries for logistic regression. The second question is given the logistic regression model, how do we fit $\theta$ for it? We use the maximum likelihood estimator under a set of probabilistic assumptions, and then fit the parameters via maximum likelihood. Let us go over each of the answer in detail.

---
