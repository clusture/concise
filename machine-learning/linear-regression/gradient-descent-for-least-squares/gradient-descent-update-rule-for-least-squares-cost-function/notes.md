---
title: Gradient Descent Update Rule for Least Squares Cost
topic: Linear Regression
---

## Gradient Descent Update Rule for Least Squares Cost

Let us consider gradient descent algorithm. It starts with some initial $\theta$ and repeatedly performs the following update :  $$\theta_{j} = \theta_{j} - \alpha \frac{\partial}{\partial \theta_{j}} J(\theta),\,\,\, j = 0,1,\ldots,d$$

Here, $\alpha$ is called the learning rate. This is a very natural algorithm that repeatedly takes a step in the direction of steepest decrease of $J$. The vector form of the gradient descent rule is given by : $$\theta = \theta - \alpha \nabla_{\theta} J(\theta)$$

Here, the gradient is given by  $\nabla_{\theta} J(\theta) = {\begin{bmatrix}\frac{\partial J(\theta)}{\partial \theta_{0}}\\\frac{\partial J(\theta)}{\partial \theta_{1}}\\\vdots \\\frac{\partial J(\theta)}{\partial \theta_{d}}\end{bmatrix}}$

---