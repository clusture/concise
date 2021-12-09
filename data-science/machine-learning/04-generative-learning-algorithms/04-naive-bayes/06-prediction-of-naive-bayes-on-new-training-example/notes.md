---
title: Prediction of Naive Bayes on New Training Example
topic: Naive Bayes
slug: prediction-naive-bayes-new-training-example
---

# Prediction of Naive Bayes on New Training Example

Having fit all these parameters, to make a prediction on a new example
with features $x$ ( which is new email word vector representation), we then simply calculate :
$$\begin{aligned} p(y=1 | x) &= \frac{p(x|y=1) p(y =1)}{p(x)} \\
& = \frac{ \left[\prod_{i=1}^m p(x^i|y=1)\right] p(y=1)}{\left[\prod_{i=1}^m p(x^i|y=1)\right] p(y=1) + \left[\prod_{i=1}^m p(x^i|y=0)\right] p(y=0)}\end{aligned}$$

$p(y=1 | x)$ is the posterior probability which indicates how likely the given email is spam. Similarly, we can compute $p(y=0 | x)$ which corresponding to posterior probability of how likely email is non spam.

Once we compute $p(y=1 | x)$ and $p(y=0 | x)$, we pick whichever class has the higher posterior probability. For example, if $p(y=1 | x) > p(y=0 | x)$, then email gets classified as spam in naive bayes algorithm.







