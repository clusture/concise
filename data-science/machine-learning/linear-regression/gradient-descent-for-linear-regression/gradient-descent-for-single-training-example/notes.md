---
title: Gradient Descent for Single Training Example
topic: Gradient Descent for Linear Regression
---

# Gradient Descent for Single Training Example

In order to implement gradient descent algorithm, we need to figure out the partial derivative term $\frac{\partial}{\partial \theta_{j}}$ on the right hand size. For now, let us assume that, we have only one training example $(x,y)$, then we have : $$\begin{aligned}\frac{\partial}{\partial \theta_{j}} &= \frac{\partial}{\partial \theta_{j}} \frac{1}{2} (h_{\theta}(x) - y)^{2} \\ &= 2 . \frac{1}{2} (h_{\theta}(x) - y)\frac{\partial}{\partial \theta_{j}} (h_{\theta}(x) - y)\\ &= (h_{\theta}(x) - y)\frac{\partial}{\partial \theta_{j}} \left(\sum_{i=0}^d \theta_i x_i - y \right)\\ &= (h_{\theta}(x) - y) x_j \end{aligned}$$

Here, we used the fact that $h_{\theta}(x) = \sum_{i=0}^d \theta_i x_i$. For the single training example, the gradient descent update rule is given by : $$\theta_{j} = \theta_{j} + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i}$$

This rule is called LMS update rule. LMS stands for least mean squares. We can make the following observations regarding the update rule. The magnitude of parameter $\theta$ update is directly proportional to error $(y^{i} - h_{\theta}(x^{i}))$. Closer the prediction, small is the update to current parameter.
