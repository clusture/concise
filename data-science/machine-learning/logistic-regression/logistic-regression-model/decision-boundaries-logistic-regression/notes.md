---
title: Decision Boundary for Logistic Regression
topic: Logistic Regression Model
slug: decision-boundary
---

# Decision Boundary for Logistic Regression

We know that for binary classification task, the learning algorithm need to output either $0$ or $1$ class. But, the output of logistic regression's hypothesis function is between $0$ and $1$. In order to get our discrete $0$ or $1$ classification, we can translate the output of the hypothesis function as follows: $$\begin{aligned} h_{\theta}(x) \ge 0.5 &\implies y=1 \\ h_{\theta}(x) < 0.5 &\implies y=0 \end{aligned}$$

Recall the hypothesis function of logistic regression $h_{\theta}(x) = g(\theta^Tx)$. Let us look one of the property of logistic function $g$. The logistic function $g(z) \ge 0.5$ only if $z \ge 0$. We can use this property to find when $h_{\theta}(x) \ge 0.5$ and use that to assign a class label $0$ or $1$. We know that $h_{\theta}(x) = g(\theta^T x)$. Hence, $h_{\theta}(x) \ge 0.5$ implies $g(\theta^T x) \ge 0.5$ and from the sigmoid property we know that this implies $\theta^T x \ge 0$. When $\theta^T x \ge 0$ : $$\begin{aligned}\theta^Tx \ge 0 &\implies y=1 \\ \theta^Tx < 0 &\implies y=0\end{aligned}$$

The decision boundary is the line that separates the area where $y = 0$ and where $y = 1$. It is created by our hypothesis function using the equation: $$\begin{aligned}h_{\theta}(x) &= 0.5 \\ \text{or,}\,\, \theta^Tx &=0\end{aligned}$$
