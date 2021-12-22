---
title: Regularization
topic: Learning Theory Topics
slug: regularization
---

# Regularization

We understood that sometimes model performs well on the training data but does not perform well on the unseen or test data. It means the model is not able to predict the output or target column for the unseen data. We know that such model is called an overfitted model. Regularization is one of the technique to control the overfitting.

Regularization technique aims at reducing the variance to obtain a robust model. By controlling the variance of the model, they control the overfitting. Common form of regularization is add a term to the objective function to penalize the model complexity.

In supervised machine learning, the goal is to learn a function $f$ that minimizes some form a loss function. The common form of regularization is given by :
$${\underset {f} {\operatorname {min}}} \sum _{i=1}^{n} \mathcal{L}(f(x^i), y^i) + \lambda R(f)$$

Here, $\mathcal{L}$ is the loss function and $\lambda$ is the regularization parameter. And, $R(f)$ is a regularization term. Let us look at this form of regularization in a specific context.

In the case of mean square error/loss function, and when the regularization term is the sum of the squared weights. The optimization problem is given by :
$${\underset {\theta \in \mathbb{R}^d} {\operatorname {\text{arg min}}}} \sum_{i=1}^m (h_{\theta}(x^i) - y^i)^2 + \lambda \|\theta\|^2$$

Here, $\|\theta\|^2$ is the sum of the squared weights. It is given by $\|\theta\|^2 = \theta_1^2 + \theta_2^2+ \dots + \theta_d^2$.
This form of regularization is called L2 regularization as $\|\theta\|$ is called as L2 norm. L2 regularization is a form of regularization that penalizes the model complexity and reduces the model weights from attaining a bigger values.

If the $h_{\theta}(x)$ is a linear function of the form $\theta^t x$ as in the case of linear regression, then this is called as **Ridge regression**.

Another popular form of regularization is L1 regularization. L1 regularization is a form of regularization that penalizes the model complexity and reduces the model weights from attaining a bigger values. It is given by :
$${\underset {\theta \in \mathbb{R}^d} {\operatorname {\text{arg min}}}} \sum_{i=1}^m (h_{\theta}(x^i) - y^i)^2 + \lambda \,\,|\theta|$$

Here, $|\theta|$ is a absolute value of sum of weights. It is given by $|\theta_1 + \theta_2 + \ldots + \theta_d|$. It is also known as L1 norm. In the case of the linear regression, the model resultant of this form of regularization is called **Lasso regression**.


Let us look at how regularization reduces the variance of the model and helps reduce the overfitting. The regularization terms discussed above controls the model weights from attaining a bigger values. Hence, they might not fit to noise or inaccuracies in the data even when the model is complex. This controls the variance of the model and reduces the overfitting.
