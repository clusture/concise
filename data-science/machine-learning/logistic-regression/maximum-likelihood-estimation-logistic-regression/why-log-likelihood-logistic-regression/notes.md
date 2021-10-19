---
title: Why Log Likelihood: Logistic Regression
topic: Maximum Likelihood Estimation: Logistic Regression
slug: why-log-likelihood
---

# Why Log Likelihood: Logistic Regression

We need to answer two questions before proceeding with optimizing log likelihood :
1. Why log likelihood is a easier optimization problem to solve ?
2. And what is the guarantee that the optimal parameter obtained solving log likelihood is same as that of optimal parameter for solving likelihood ?

Let us recall both likelihood and log likelihood functions of logistic regression : 
$$\mathcal{L}(\theta) = \prod_{i=1}^n (h_{\theta}(x^i))^{y^i} (1-h_{\theta}(x^i))^{1-y^{i}}$$
$$l(\theta) = \sum_{i=1}^n y^i\,log (h_{\theta}(x^i)) + (1-y^{i}) \, log\,(1-h_{\theta}(x^i))$$

Let us answer each of the questions separately. First, let us look at why the log likelihood is a easier function to optimize. So it is not necessary to put  log  to solve the problem. It is done because most of the times its quicker to deal with sums than the products in the objective since it is more convenient to differentiate the sums than products for optimization.

Second, let us look whether both likelihood and log likelihood optimization problems give same result or not. $log ()$ is an increasing function. So, $log(x)$ will be maximum for the element $x$ if it is maximum among others in the set. $l(\theta)$ will be maximum when $\mathcal{L}(\theta)$ is maximum. Hence, the $\theta$ that maximizes the $\mathcal{L}(\theta)$ will also maximizes $l(\theta)$. Therefore, the two optimization problems, one with $l(\theta)$ and another with $\mathcal{L}(\theta)$ gives the same result.

Now let us look, how to find the optimal parameter for the log likelihood function.

---
