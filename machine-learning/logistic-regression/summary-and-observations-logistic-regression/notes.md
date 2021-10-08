---
title:  Summary and Observations: Logistic Regression
topic: Logistic Regression
---

## Summary and Observations: Logistic Regression

We formally described the classification problem under supervised learning settings. We introduced logistic regression model for binary classification problem. Logistic regression due to its relative simplicity and well-known properties is one of the popular techniques in machine learning. We used maximum likelihood estimation for finding the optimal parameter for logistic regression. We used gradient ascent iterative scheme to find the optimal parameter. 

The following are the few observations. If we compare parameter update rule of logistic regression to the ordinary mean squared update rule of linear regression then we can see that both look identical. That is, the update rule looks like : $$\theta_j = \theta_j + \alpha (y^i - h_{\theta}(x^i))x_j$$

But both are not the same algorithms, because $h_{\theta}(x)$ is defined as a non-linear function $\theta^T x$, which is given by $g(\theta^T x)$. Nonetheless, it's a little surprising that we end up with the same update rule for a rather different algorithm and learning problem. One can find the deeper reason behind this in generalized linear models (GLMs).

Another interesting observation is regarding the choice of $g$ in the hypothesis function. Other functions that smoothly increase from 0 to 1 can also be used. But, the choice of the logistic function is a fairly natural one. However, the reasons for that can be found in GLMs and generative learning algorithms.

---



