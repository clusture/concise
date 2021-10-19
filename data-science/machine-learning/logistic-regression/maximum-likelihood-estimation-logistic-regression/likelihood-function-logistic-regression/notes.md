---
title: Likelihood Function for Logistic Regression
topic: Maximum Likelihood Estimation: Logistic Regression
slug: likelihood-func
---

# Likelihood Function for Logistic Regression

Before moving to the maximum likelihood estimation, let us define some things required for estimating the optimal parameter through maximum likelihood estimation for logistic regression.

Let us assume that : $$\begin{aligned}p(y=1|x;\theta) &= h_{\theta}(x), \\ \text{And,}\,\, p(y=0|x;\theta) &= 1- h_{\theta}(x)\end{aligned}$$

Note that this can be written more compactly as : $$p(y|x;\theta)=(h_{\theta}(x))^y (1-h_{\theta}(x))^{1-y}$$

Assuming that the $n$ training examples were generated independently, we can then write down the likelihood of the parameters as : $$\begin{aligned}\mathcal{L}(\theta) &= p( {\vec y}|x;\theta) \\&= \prod_{i=1}^n p(y^i|x^i;\theta)\\ &= \prod_{i=1}^n (h_{\theta}(x^i))^{y^i} (1-h_{\theta}(x^i))^{1-y^{i}} \end{aligned}$$

The goal of maximum likelihood estimation is to find the values of the model parameters that maximize the likelihood function : $${\underset {\theta} {\operatorname {max}}}\quad \mathcal{L}(\theta) = \prod_{i=1}^n (h_{\theta}(x^i))^{y^i} (1-h_{\theta}(x^i))^{1-y^{i}}$$

Let us look at how to find the optimal parameter or Is there a easy way of solving another simpler optimization problem to get the same optimal parameter.

---
