---
title: LMS Algorithm with Batch Gradient
topic: Gradient Descent for Linear Regression
---

## LMS Algorithm with Batch Gradient

So far, we have looked the case where training set has only one example. Let us looks for the ways to generalize the update rule for the cases where training set having more than one training example. One way to modify the update rule to work with more than one training example is the following 

$$\begin{aligned}
&\text{repeat until convergence}\,\, \{ \\
&\theta_{j} = \theta_{j} + \alpha \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^{i})) x_{j}^{i},\,\, \text{(for every j)} \\
&\}
\end{aligned}
$$

We can write the above algorithm in vector form as following : $$\theta = \theta + \alpha \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^i)) x^{i}$$

This method looks at each and every training example on the training set for every step and computes the gradient and updates the parameter $\theta$. This update rule is called **batch gradient descent**. Gradient descent can be suspectable to local minima in general. However, the optimization problem that we have formulated here has one global minima and no local minima. Thus, gradient descent always converges to local minima.

---