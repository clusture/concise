---
title: Gradient Ascent Update: Logistic Regression
topic: Maximum Likelihood Estimation: Logistic Regression
---

# Gradient Ascent Update: Logistic Regression

Let us recall the optimization problem corresponding to the log likelihood : $${\underset {\theta} {\operatorname {max}}} \,\,\,l(\theta) = \sum_{i=1}^n y^i\,log (h_{\theta}(x^i)) + (1-y^{i}) \, log\,(1-h_{\theta}(x^i))$$

How do we maximize the likelihood? We can use gradient ascent. Written in vectorial notation, our updates will therefore be given by $$\theta := \theta + \alpha \nabla_{\theta} l(\theta)$$

Note the positive rather than negative sign in the update formula, since we're maximizing a function now. Let's start by working with just one training example $(x, y)$, and take derivatives to derive the stochastic gradient ascent rule : 

$$\begin{aligned}\frac{\partial}{\partial \theta_j} l(\theta_j) &= \left(y \frac{1}{g(\theta^Tx)} - (1-y) \frac{1}{(1-g(\theta^T x))}\right) \frac{\partial}{\partial\theta_j} g(\theta^T x) \\&= \left(y \frac{1}{g(\theta^Tx)} - (1-y) \frac{1}{(1-g(\theta^T x))}\right) g(\theta^T x) (1-g(\theta^T x))\,\, \frac{\partial}{\partial \theta_j}\theta^T x \\&= (y(1-g(\theta^Tx)) - (1-y)g(\theta^Tx))x_j \\&= (y - h_{\theta}(x))x_j\end{aligned}$$

Above, we used the fact that : $g'(z) = g(z)(1-g(z))$.  This therefore gives us the stochastic gradient ascent rule : $$\theta_j = \theta_j + \alpha (y^i - h_{\theta}(x^i))x_j$$


---