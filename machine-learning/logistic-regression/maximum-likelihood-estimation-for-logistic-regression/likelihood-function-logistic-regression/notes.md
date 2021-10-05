---
title: Likelihood Function for Logistic Regression
topic: Maximum Likelihood Estimation for Logistic Regression
---

## Likelihood Function for Logistic Regression

Before moving to the maximum likelihood estimation, let us define some things required for estimating the optimal parameter through maximum likelihood estimation for logistic regression. 

Let us assume that : $$\begin{aligned}p(y=1|x;\theta) &= h_{\theta}(x), \\ \text{And,}\,\, p(y=0|x;\theta) &= 1- h_{\theta}(x)\end{aligned}$$

Note that this can be written more compactly as : $$p(y|x;\theta)=(h_{\theta}(x))^y (1-h_{\theta}(x))^{1-y}$$


For now, let's take the choice of $g$ as given. Other functions that smoothly increase from 0 to 1 can also be used, but for a couple of reasons that we'll see later (when we talk about GLMs, and when we talk about generative learning algorithms), the choice of the logistic function is a fairly natural one.

---
