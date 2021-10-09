---
title: Gradient Descent for Least Squares Cost
topic: Gradient Descent for Linear Regression
---

# Gradient Descent for Least Squares Cost

There are alternatives to batch gradient descent. Consider the following iterative algorithm : 
$$\begin{aligned}
&\text{Loop}\,\, \{ \\
&\text{for i = 1 to n, }\,\, \{ \\
&\theta_{j} = \theta_{j} + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i},\,\, \text{(for every j)} \\
&\}
&\}
\end{aligned}
$$

By grouping the updates of coordinates into update of the vector $\theta$, we can rewrite the above rule into : $$\theta = \theta + \alpha (y^{i} - h_{\theta}(x^{i})) x^{i}$$

This algorithm is called **stochastic gradient descent** (also incremental gradient descent).

---