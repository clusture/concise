---
title: Gradient Descent for Linear Regression
topic: Linear Regression
slug: gradient-descent
---

# Gradient Descent for Linear Regression

We want to find $\theta$ that minimizes least squares cost function $J(\theta)$. We want to solve the optimization problem which is formulated as: $${\underset {\theta} {\operatorname {max}}}\quad J(\theta) = \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(x^{i}) - y^{i})^{2}$$

In order find optimal $\theta$, we can use the learning algorithm that starts with some initial guess for $\theta$, and that repeatedly changes $\theta$ after each iteration to make $J(\theta)$ smaller and we reach a $\theta$ that minimizes the $J(\theta)$. One such technique is called gradient descent algorithm. Let us look more details about gradient descent algorithm for linear regression next.

---
