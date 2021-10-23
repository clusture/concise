---
title: Least Squares Regression Optimization Problem
topic: Ordinary Least Squares Regression
slug: least-squares-regression-optimization-problem
---

# Least Squares Regression Optimization Problem

We have seen the least squares cost function which measures the difference between prediction $h_{\theta}(x)$ and actual value $y$. We want this cost to be as low as possible atleast for a given training set. In order to do that, we need to choose $\theta$ that minimizes $J(\theta)$. This ideas can be captured in optimization framework by defining appropriate optimization problem. The optimization problem is given by: $${\underset {\theta} {\operatorname {min}}}\quad J(\theta) = \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(x^{i}) - y^{i})^{2}$$

Now, how to learn the optimal parameter $\theta$ that minimizes the least square cost function? 
