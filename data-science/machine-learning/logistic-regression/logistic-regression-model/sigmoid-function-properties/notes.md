---
title: Sigmoid Function Properties
topic: Logistic Regression Model
slug: sigmoid-func-props
---

# Sigmoid Function Properties

Sigmoid functions has few interesting properties that make more usable in machine learning and deep learning. Let us discuss some of them. Let us recall the sigmoid function : $$g(z) = \frac{1}{1+e^{-z}}$$

Notice that $g(z)$ value goes to 1 as $z \to \infty$ and $g(z)$ value goes to 0 as $z \to -\infty$. 

Moreover, $g(z)$ is always bounded between 0 and 1. As before, we are keeping the convention of letting $x_0 = 1$ so that $\theta^Tx = \theta_0 + \sum_{j=1}^d \theta_j x_j$.

Before moving on, here's a useful property of the derivative of the sigmoid function, which we write as $g'$ : $$\begin{aligned}g'(z) &= \frac{d}{dz}\,\,\frac{1}{1+e^{-z}} \\&= \frac{1}{(1+e^{-z})^2} (e^{-z}) \\&= \frac{1}{(1+e^{-z})} \left(1 - \frac{1}{(1+e^{-z})}\right) \\&= g(z)(1-g(z))\end{aligned}$$

This shows that the derivative of sigmoid function $g(z)$ can be expressed as function of sigmoid function itself $g(z)$. It is very useful property.
