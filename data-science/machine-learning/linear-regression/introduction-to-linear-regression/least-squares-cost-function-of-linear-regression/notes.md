---
title: Least Squares Cost Function of Linear Regression
topic: Introduction to Linear Regression
slug: least-squares-cost-func
---

# Least Squares Cost Function

For a given training set, how do we pick or learn the parameter $\theta$ ? The idea here is to make $h(x)$ as much as close to $y$, atleast for the training examples that we have.

The idea is to define the cost function that measures the distance between $h(x^i)$ and $y^i$ for each example $x^i$ in the training set for a given value of parameter $\theta$. The cost function is given by : $$J(\theta) = \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(x^{i}) - y^{i})^{2}$$

In linear regression, this cost function is called **least squares cost function**. This gives raise to **ordinary least squares** regression model. 

Using this least squares cost function, we need to learn the parameter $\theta$ that minimizes cost over atleast for training set.

---
