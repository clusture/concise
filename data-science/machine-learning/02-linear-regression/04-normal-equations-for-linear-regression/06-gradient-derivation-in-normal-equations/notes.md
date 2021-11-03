---
title: Gradient Derivation for Normal Equations
topic: Normal Equations for Linear Regression
slug: gradient-derivation-normal-eqn
---

# Gradient Derivation for Normal Equations

Recall that, we use gradient descent algorithm for finding the optimal parameter $\theta$ which minimize the cost function $J(\theta)$. We use the similar approach now. However, we can use the matrix notation of the least squares cost function to compute the gradient. Recall the matrix notation of least squares cost function given by :
$$J(\theta) = \frac{1}{2} (X\theta - {\vec y})^{T}(X\theta - {\vec y})$$

The gradient of least squares cost function $J(\theta)$ is given by :
$$\begin{aligned}\nabla_{\theta} J(\theta) &= \nabla_{\theta}\frac{1}{2} (X\theta - {\vec y})^{T}(X\theta - {\vec y}) 
\\ &= \frac{1}{2} \nabla_{\theta} \left((X\theta)^T(X \theta) - (X\theta)^T{\vec y}) - {\vec y}^T(X\theta) + {\vec y}^T{\vec y}\right)
\\ &= \frac{1}{2} \nabla_{\theta} \left(\theta (X^TX) \theta - {\vec y}^T(X\theta) - {\vec y}^T(X\theta) \right)
\\ &= \frac{1}{2} \nabla_{\theta} \left(\theta (X^TX) \theta -2\,\,(X^T {\vec y})^T \theta \right)
\\ &= \frac{1}{2} \left(2\,\,(X^TX) \theta -2\,\,(X^T {\vec y}) \right)
\\ &= X^{T}X \theta - X^{T}y\end{aligned}$$

We used the following results in the above derivation. In the third step, $\nabla_{\theta} {\vec y}^T{\vec y} = 0$ and $a^Tb = b^Ta$. And, in the fifth step used the facts $\nabla_{x} b^Tx = b$ and $\nabla_{x} x^T A x = 2Ax$ for symmetric matrix $A$. 
