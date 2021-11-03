---
title: Stochastic Gradient Descent for Linear Regression
topic: Gradient Descent for Linear Regression
slug: stochastic-gradient-descent
---

# Stochastic Gradient Descent for Linear Regression

There are alternatives to batch gradient descent. Instead of looking at all the training examples to update the parameter. Consider the following iterative algorithm, where parameter update is performed for every training example : 
$$\begin{aligned}
&\text{Loop}\,\, \{ \\
&\text{for i = 1 to n, }\,\, \{ \\
&\theta_{j} = \theta_{j} + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i},\,\, \text{(for every j)} \\
&\}
&\}
\end{aligned}
$$

By grouping the updates of coordinates into update of the vector $\theta$, we can rewrite the above rule into :
$$\theta = \theta + \alpha (y^{i} - h_{\theta}(x^{i})) x^{i}$$

This algorithm is called **stochastic gradient descent** (also incremental gradient descent).
