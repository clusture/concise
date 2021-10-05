---
title: Logistic Regression Model
topic: Logistic Regression Model
---

## Logistic Regression Model

Let us recall the hypothesis function of logistic regression algorithm : $$\begin{aligned} h_{\theta}(x) &= g(\theta^{T}x) \\&= \frac{1}{1 + e^{\theta^T x}}\end{aligned}$$

We know that $h_{\theta}(x)$ is always bounded between 0 and 1 due to property of sigmoid function $g$. We are keeping the convention of letting $x_0 = 1$ so that $\theta^Tx = \theta_0 + \sum_{j=1}^d \theta_j x_j$.

So, given the logistic regression model, how do we fit $\theta$ for it? We use the maximum likelihood estimator under a set of probabilistic assumptions, and then fit the parameters via maximum likelihood. 

---