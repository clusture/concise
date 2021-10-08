---
title: Logistic Regression's Hypothesis Function
topic: Logistic Regression Model
---

## Logistic Regression's Hypothesis Function

For binary classification tasks, intuitively it also doesn't make sense for $h_{\theta} (x)$ to take values larger than 1 or smaller than 0 when we know that $y \in \{0,1\}$. We know that linear regression can give any value between $(-\infty, \infty)$.

To fix it let's change the form of a hypotheses function $h_{\theta}(x)$. We will chose : $$\begin{aligned} h_{\theta}(x) &= g(\theta^{T}x) \\&= \frac{1}{1 + e^{\theta^T x}}\end{aligned}$$

Here, function $g$ is called logistic function or sigmoid function. This forms the hypotheses function of logistic regression model. Let us look the details of sigmoid function.

---