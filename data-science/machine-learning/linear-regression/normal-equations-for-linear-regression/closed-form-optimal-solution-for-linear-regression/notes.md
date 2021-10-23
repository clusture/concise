---
title: Closed Form Optimal Solution for Linear Regression
topic: Normal Equations for Linear Regression
slug: closed-form-optimal-soln
---

# Closed Form Optimal Solution for Linear Regression

When we derived the gradient of least squares cost function in the matrix notation and equated it to zero to solve for optimal parameter, we got set of equations called normal equations. Those are give by : $$X^{T}X \theta = X^{T}{\vec y}$$

We get the closed form expression for the parameter $\theta$ after solving the normal equations. The parameter value that minimizes $J(\theta)$ is given in closed form by the equation : $$\theta^{*} = (X^{T}X)^{-1}X^{T}{\vec y}$$
