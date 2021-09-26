---
title: Logistic Regression
topic: Logistic Regression
---

# Newtons method

Newtons method is for finding zeros of a function

Problem Statement : Given function $f$, find $\theta$ such that $f(\theta) = 0$

Parameter update rule for Newtons method $$\theta := \theta - \frac{f(\theta)}{f'(\theta)}$$

---

## Logistic Regression

In logistic regression :
* Want to maximize log likelihood $l(\theta)$, 
* i.e find $\theta$ such that $l'(\theta) = 0$

Can we use Newtons method ?
* What Newtons method gives is $f(\theta) = 0$
* What we want $\theta$ that maximize $l(\theta)$

---

## Newtons method for Logistic Regression

Maxima of log likelihood function $l$ corresponds to points where $l'(\theta) = 0$

Let $f(\theta) = l'(\theta)$ and use Newtons method for finding $\theta$

Update Rule for Logistic Regression $$\theta := \theta - \frac{l'(\theta)}{l''(\theta)}$$

---

## Newtons method for multi-dimensional

Update Rule for Multi-dimensional setting : $$\theta := \theta - H^{-1}\nabla_{\theta} l(\theta)$$

Here :
* $\nabla_{\theta} l(\theta)$ vector of partial derivative for $l(\theta)$ wrt $\theta_{i}'s$
* $H$ is a $(d+1 \times d+1)$ dimensional Hessian matrix
* $H_{ij} = \frac{\partial^2 l(\theta)}{\partial \theta_i \partial \theta_j}$

---

## Advantages and Disadvantages of Newtons method

Advantages :
* Faster Convergence
* Very few iterations to get close to minimum

Disadvantages :
* More expensive due to Hessian matrix inversion for every iteration

---
