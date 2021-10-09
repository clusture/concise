---
title: Decision Boundary: Logistic Regression
topic: Logistic Regression Model
---

# Decision Boundary: Logistic Regression

We know that for binary classification task, the learning algorithm need to output either $0$ or $1$ class. But, the output of logistic regression's hypothesis function is between $0$ and $1$. In order to get our discrete $0$ or $1$ classification, we can translate the output of the hypothesis function as follows: $$\begin{aligned} h_{\theta}(x) \ge 0.5 &\implies y=1 \\ h_{\theta}(x) < 0.5 &\implies y=0 \end{aligned}$$

Recall the hypothesis function of logistic regression $h_{\theta}(x) = g(\theta^Tx)$. Let us look one of the property of logistic function $g$. The logistic function $g(z) \ge 0.5$ if $z \ge 0$. We can use this property to find when $h_{\theta}(x) \ge 0.5$. We know that $h_{\theta}(x) = g(\theta^T x)$. Hence, $h_{\theta}(x) \ge 0.5$ implies $g(\theta^T x) \ge 0.5$. if $\theta^T x \ge 0$


---