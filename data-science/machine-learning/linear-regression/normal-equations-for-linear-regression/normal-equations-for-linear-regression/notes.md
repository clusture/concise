---
title: Normal Equations Derivation for Linear Regression
topic: Normal Equations for Linear Regression
slug: normal-eqn-derivation
---

# Normal Equations Derivation for Linear Regression

We derived the matrix expression for the gradient of ordinary least squares regression. It is given by : $$\nabla_{\theta} J(\theta) = X^{T}X \theta - X^{T}y$$

In order to minimize $J(\theta)$, we need to set the derivative of it to zero and solve for it : $$X^{T}X \theta - X^{T}{\vec y} = 0$$

In our case, this translates in to **Normal equations** :$$X^{T}X \theta = X^{T}{\vec y}$$

We need to solve these set of equations to find the optimal parameter $\theta$.

---
