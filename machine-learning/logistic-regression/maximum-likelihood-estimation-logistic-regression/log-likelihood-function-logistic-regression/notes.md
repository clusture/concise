---
title: Log Likelihood Function: Logistic Regression
topic: Maximum Likelihood Estimation: Logistic Regression
---

## Log Likelihood Function: Logistic Regression

Let us recall the likelihood function of logistic regression : $$\mathcal{L}(\theta) = \prod_{i=1}^n (h_{\theta}(x^i))^{y^i} (1-h_{\theta}(x^i))^{1-y^{i}}$$

Let us look for easier way solve for optimal parameter. One way is by taking the logarithm of the likelihood function and optimizing on log of the likelihood. That is, log likelihood is given by : $$\begin{aligned}l(\theta) &= log \,\,\mathcal{L}(\theta) \\&= log \left[\prod_{i=1}^n (h_{\theta}(x^i))^{y^i} (1-h_{\theta}(x^i))^{1-y^{i}}\right] \\&=\sum_{i=1}^n y^i\,log (h_{\theta}(x^i)) + (1-y^{i}) \, log\,(1-h_{\theta}(x^i)) \end{aligned}$$

And the optimization problem corresponding to the log likelihood is given by : $${\underset {\theta} {\operatorname {max}}} \,\,\,l(\theta)$$

---
