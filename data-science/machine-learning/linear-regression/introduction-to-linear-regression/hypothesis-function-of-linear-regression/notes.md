---
title: Hypotheses Function of Linear Regression
topic: Introduction to Linear Regression
---

# Hypotheses Function of Linear Regression

To perform supervised learning, we must decide how we are going to represent functions/hypotheses $h$ in a computer. As an initial choice, let's say we decide to approximate $y$ as a **linear function** of $x$: $$h_{\theta}(x) = \theta_{0} + \theta_{1} x_{1} + \theta_{2} x_{2}$$

Here, the $\theta_i$'s are parameters (also called as weights) parameterizing the space of linear functions mapping from $\mathcal{X}$ to $\mathcal{Y}$. Let us look at, how to interpret this with respect to house prediction example. For a given home $x$, we calculate $h_{\theta}(x)$ and use it as a prediction for the price of house $x$.

To simplify the notation, let us introduce the convention of $x_0 = 1$ (intercept term) and also the drop the subscript $\theta$ from $h_{\theta}(x)$ for representing hypotheses function. Then our hypotheses function looks like : $$h(x) = \sum_{i=0}^d \theta_i x_i = \theta^T x$$

Here, both $\theta$ and $x$ are $d$ dimensional vectors. Hence, the parameter to learn is $\theta$, which is a $d$-dimensional vector in this model. 

---