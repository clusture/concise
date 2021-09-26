---
title: Linear Regression
topic: Linear Regression
---

## Supervised Learning

Linear regression is a supervised learning algorithm

The goal is to map the input variable ($x$) to a output variable ($y$)

In regression problems output variable is continuous

---

## Example

image of table

Supervised Learning :
- living areas : input variable
- prices : output variable

image of table + plot


---

## Supervised Learning Task

Notation :
* $x^{i}$ denote the --input-- variables or input --features--
* $y^{i}$ denote the --output-- or --target-- variable
* Training Example : $(x^{i},y^{i})$
* Training Set : ${(x^{i},y^{i}) : i = 1, \ldots , n}$

We are trying to predict target variable

---

## Supervised Learning Problem

Spaces : 
- $X$ denote input space
- $Y$ denote the output space
- In house prediction example $ X = Y = R (\text{real space})$

Goal: is to learn a function $h : X \to Y$ (good predictor)

image-hypothesis


---

## Regression

If target variable is continuous, we call the learning problem a regression problem

In house price prediction, we are predicting the continuous value

House price prediction is continuous problem

---

## Linear Regression Example

house price image

Here :
* Input: $x$'s are two-dimensional vectors
* $x_{1}^{i}$ is the living area
* And $x_{2}^{i}$ is number of bedrooms

To perform supervised learning, we must decide on hypotheses function h 


---

## Linear Regression Hypothesis Function

Approximate y as a linear function of x

The hypotheses function for linear regression : $$h_{\theta}(x) = \theta_{0} + \theta_{1} x_{1} + \theta_{2} x_{2}$$

---

## Generalized Hypothesis Function

Linear Regression for d dimensional input : $$h_{\theta}(x) = \sum_{j=1}^{d} \theta_{j}x_{j} = x^{T}\theta$$

---

## Cost Function

Given a training set, how to learn, the parameters $\theta$ ?

Idea: make $h(x)$ close to y (atleast for training examples)

--Cost Function-- : $J(\theta) = \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(x^{i}) - y^{i})^{2}$

$J(\theta)$ is called least squares cost function

This type of regression is called -- ordinary least squares regression model --

---

# LMS Algorithm

---

## Least Mean Squares Algorithm

LMS Optimization Problem : $$min_{\theta}\,\,\, \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(x^{i}) - y^{i})^{2}$$

How to find the optimal $\theta$ ?
* Gradient Descent Algorithm
* Normal Equation

---

## Optimization Problem

The optimization problem : $$ \text{min}_{\theta} J(\theta)$$

Terminology :
* $J$ is called the objective function
* $\theta$ is optimization parameter

---

## Gradient Descent

Gradient Descent Update Rule : $$\theta_{j} = \theta_{j} - \alpha \frac{\partial}{\partial \theta_{j}} J(\theta),\,\,\, j = 0,1,\ldots,d$$

Terminology :
* The learning rate $\alpha$
* Gradient : $\nabla_{\theta} J(\theta) = {\begin{bmatrix}\frac{\partial J(\theta)}{\partial \theta_{0}}\\\frac{\partial J(\theta)}{\partial \theta_{1}}\\\vdots \\\frac{\partial J(\theta)}{\partial \theta_{d}}\end{bmatrix}}$


---

## Optima

Optima ($\theta^{*}$) is defined as (for minimization problems) : $$\theta^{*} = \text{arg min}_{\theta} J(\theta)$$

Local Optima Vs Global Optima :
* Global minimum : function value is smaller than at all other points
* Local minimum : If function value is smaller than at nearby points

---

## Convex Vs Non Convex Function

Convex Function has single minimum (Only global minimum)

diagram 

Non convex function can have multiple local minimum

diagram

---

## Gradient Descent for Linear Regression

Gradient Descent update rule : $$\theta_{j} = \theta_{j} - \alpha \frac{\partial}{\partial \theta_{j}} J(\theta)$$

The Gradient (For single training example): 
* $\frac{\partial}{\partial \theta_{j}} J(\theta) = \frac{\partial}{\partial \theta_{j}} \frac{1}{2} (h_{\theta}(x) - y)^2$
* $ = (h_{\theta}(x) - y) x_{j}$

The update rule : $\theta_{j} = \theta_{j} + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i}$

---

## LMS update Rule

LMS update Rule (Single training example): $$\theta_{j} = \theta_{j} + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i}$$

Observations: 
* The magnitude of update is directly proportional to error : $(y^{i} - h_{\theta}(x^{i}))$
* Closer the prediction small is the update to current parameter vice versa

---

## LMS Algorithm

LMS Algorithm for training set having --more than one sample--

```algo
repeat until convergence {
$\theta_{j} = \theta_{j} + \alpha \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^{i})) x_{j}^{i}$, (for every j)
}
```
---

## LMS Algorithm

LMS Algorithm in a vector form for $\theta$

```algo
repeat until convergence {
$\theta = \theta + \alpha \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^{i})) x^{i}$
}
```

Here: $\frac{\partial}{\partial \theta_j} (J(\theta)) = \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^{i})) x^{i}$

---

## Batch Gradient Descent

Batch Gradient Descent Update Rule : $$\theta = \theta + \alpha \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^{i})) x^{i}$$

Observation : For every update looks at the all the training examples

---

## Convex Quadratic Objective

The least mean squared cost objective is quadratic

Least mean squared functions :
* Is convex quadratic function
* Have single global minimum

Objective function has only --one optima-- (global optima)

---

## Convergence

Gradient descent for linear regression :
* converges to global optima
* due to quadratic convex function

image for contours

image for actual line fitting to the house dataset

---

## Stochastic Gradient Descent

Batch Gradient Descent :
* every update looks at the all the training examples
* Costly operation if training set is large

Can we update the parameter more often ? :
* Stochastic Gradient Descent

---

## Stochastic Gradient Descent

```algo
Loop {
    for i = 0 to n, {
$\theta = \theta + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i}, \text{for every j}$
    }
}
```

Update in Vector form : $$\theta = \theta + \alpha (y^{i} - h_{\theta}(x^{i})) x^{i}$$

---

## Stochastic Gradient Descent

Stochastic Gradient :
* Updates the parameter for every training example
* Starts making progress right away
* Parameter update reaches close to the local minimum much faster
* Oscillates around the minimum of $J(\theta)$

---

# The Normal Equations

Recall LMS Optimization Problem : $$min_{\theta}\,\,\, \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(x^{i}) - y^{i})^{2}$$

Is there another way of finding the $\theta$ other than Gradient Descent ?

---

## Derivatives

Recall the Gradient :
$\nabla_{\theta} J(\theta) = {\begin{bmatrix}\frac{\partial J(\theta)}{\partial \theta_{0}}\\\frac{\partial J(\theta)}{\partial \theta_{1}}\\\vdots \\\frac{\partial J(\theta)}{\partial \theta_{d}}\end{bmatrix}}$

---

## Matrix Derivatives

Let Function $ f : R^{n \times d} \to R$

Matrix Derivatives : $$\mathrm {A} ={\begin{bmatrix}A_{11}&A_{12}&\cdots &A_{1d}\\A_{21}&A_{22}&\cdots &A_{2d}\\\vdots &\vdots &\ddots &\vdots \\A_{n1}&A_{n2}&\cdots &A_{nd}\end{bmatrix}} \quad \text{and }\quad \nabla_{A} f(A) = {\begin{bmatrix}\frac{\partial f}{\partial A_{11}}&\frac{\partial f}{\partial A_{12}}&\cdots &\frac{\partial f}{\partial A_{1d}}\\\frac{\partial f}{\partial A_{21}}&\frac{\partial f}{\partial A_{22}}&\cdots &\frac{\partial f}{\partial A_{2d}}\\\vdots &\vdots &\ddots &\vdots \\\frac{\partial f}{\partial A_{n1}}&\frac{\partial f}{\partial A_{n2}}&\cdots &\frac{\partial f}{\partial A_{nd}}\end{bmatrix}}$$

---

## Supervised Learning Matrix Notation

Let $x_{1}, x_{2}, \ldots , x_{n}$ be the training examples

Matrix for training set (Design Matrix) : $ X={\begin{pmatrix} \dots (\mathbf {x}^{1})^{\mathsf {T}}\dots\\ \dots(\mathbf {x}^{2})^{\mathsf {T}}\dots\\\vdots \\\dots(\mathbf {x}^{n})^{\mathsf {T}}\dots\end{pmatrix}}
={\begin{pmatrix}1&x_{11}&\cdots &x_{1p}\\1&x_{21}&\cdots &x_{2p}\\\vdots &\vdots &\ddots &\vdots \\1&x_{n1}&\cdots &x_{np}\end{pmatrix}} $

---

## Supervised Learning Matrix Notation

Let y be the vector consists of target variable (actual):
$\mathbf {y} ={\begin{pmatrix}y^{1}\\y^{2}\\\vdots \\y^{n}\end{pmatrix}} $

Recall linear regression Hypothesis function : $$h_{\theta}(x) = \sum_{j=1}^{d} \theta_{j}x_{j} = x^{T}\theta, \quad \text{predicted target variable}$$

---

## Supervised Learning Matrix Notation

Let the vector : $$X\theta - y = {\begin{pmatrix}  (\mathbf {x}^{1})^{\mathsf {T}}\theta\\ (\mathbf {x}^{2})^{\mathsf {T}}\theta\\\vdots \\(\mathbf {x}^{n})^{\mathsf {T}}\theta\end{pmatrix}} - {\begin{pmatrix}y^{1}\\y^{2}\\\vdots \\y^{n}\end{pmatrix}} = {\begin{pmatrix}  \mathbf {h_{\theta}(x^{1}) - y^{1}}\\ \mathbf {h_{\theta}(x^{2}) - y^{2}}\\\vdots \\\mathbf {h_{\theta}(x^{n}) - y^{n}}\end{pmatrix}}$$

For a vector $z$, we know that :  $z^{T}z = \sum_{i}z_{i}^2$

---

## Cost Function in Matrix Form

Least Squares Cost Function for Linear Regression : $$ J(\theta) = \frac{1}{2} (X\theta - y)^{T}(X\theta - y) = \frac{1}{2} \sum_{t}^{n} (\mathbf {h_{\theta}(x^{i}) - y^{i}})^{2}$$

To minimize $J(\theta)$, the gradient is $$\nabla_{\theta} J(\theta) = \nabla_{\theta}\frac{1}{2} (X\theta - y)^{T}(X\theta - y)$$

---

## Closed form Expression

After Algebraic manipulations : $$\nabla_{\theta} J(\theta) = \nabla_{\theta}\frac{1}{2} (X\theta - y)^{T}(X\theta - y)\\= X^{T}X \theta - X^{T}y$$

To get minimum parameter :
* Equating the gradient to zero $$X^{T}X \theta - X^{T}y = 0$$
* Solve for parameter $\theta$ : $$\theta = (X^{T}X)^{-1}X^{T}y$$

---

## Optimal Parameter

The optimal parameter $\theta$ that minimizes the $J(\theta)$ is given by : $$\theta^{*} = (X^{T}X)^{-1}X^{T}y$$

---

# Locally Weighted Regression

What if the data is not fit by a straight line ?

diagram

Types of Learning Algorithms :
* Parameter Learning Algorithm
* Non Parametric Learning Algorithm


---

## Parametric Learning Algorithm

Parametric Learning Algorithm
* Fit fixed set of learning algorithms to data
* E.g : Linear Regression

---

## Non Parametric Learning Algorithm

Non Parametric Learning Algorithm
* Amount of data or parameters you need to keep grows linearly wrt training set size
* Need to keep the lot of data in memory 
* Not feasible for large data set problems
* Locally Weighted Regression

---

## Locally Weighted Regression

Modify the cost function of linear regression

Fit $\theta$ to minimize : $$\frac{1}{2} \sum_{t}^{n} w^{i}(\mathbf {h_{\theta}(x^{i}) - y^{i}})^{2}$$

Here, $w^{i}$ is weight function

---

## Weight Function

Common choice for weight function is : $$w^{i} = exp\left(- \frac{(x^{i}-x)^{2}}{2}\right)$$

Tells how much attention to pay for training example $(x^{i},y^{i})$

If $|x - x^{i}|$ is small then $w^{i} \approx 1$

If $|x - x^{i}|$ is large then $w^{i} \approx 0$

---

## Modification to weight function

Full weight function : $$w^{i} = exp\left(-\frac{(x^{i}-x)^{2}}{2 \tau^{2}}\right)$$

$\tau$ is called :
* Bandwidth parameter 
* Decides how many nearby examples to look to consider

---

## Advantages

Locally Weight Linear Regression is useful when the dimensionality is low

useful for non linear datasets

---

# Probabilistic Interpretation of Linear Regression

Why the least squares cost function ?

Assume true value of target variable : $$y^{i} = \theta^{T}x^{i} + \epsilon^{i}$$

$\epsilon^{i}$ is error term, captures :
* Un modelled effects
* Random Noise

---

## Assumptions

Assume :
* $\epsilon^{i} \sim \mathcal{N}(0, \sigma^{2})$ 
* And $\epsilon^{i}$ are I.I.D

Probability Density Function : $$Pr(\epsilon^{i}) = \frac{1}{\sqrt{2\pi}\sigma} -exp\left(\frac{(\epsilon^{i})^{2}}{2 \sigma^{2}}\right)$$

---

## Probabilistic Interpretation

Probability density function of target variable : $$Pr(y^{i} | x^{i}; \theta) = \frac{1}{\sqrt{2\pi}\sigma} exp\left(- \frac{(y^{i}-\theta^{T}x^{i})^{2}}{2 \sigma^{2}}\right)$$

Here, --$;$-- reads as "parameterized by"

In other words, the probability of target variable $$ y^{i} | x^{i}; \theta \sim \mathcal{N}(\theta^{T}x^{i}, \sigma^{2})$$

---

## Probabilistic Interpretation

What is the distribution of the target variable $y$ ? Given :
- Design Matrix $X$ 
- And parameter $\theta$
- Given by $Pr(y|X;\theta)$ 

$Pr(y|X;\theta)$ is viewed as a function of $y$ and X for a fixed $\theta$

---

## Likelihood

Likelihood is when $Pr(y|X;\theta)$ is viewed as a function of $\theta$

Likelihood is given by : $$\mathcal{L}(\theta) = Pr(y | X; \theta) = \displaystyle\prod_{i=1}^{n}Pr(y^{i} | x^{i}; \theta)$$

---

## Likelihood

Likelihood is a function of varying parameters while holding the data fixed

The final expression for Likelihood is given by : $$\mathcal{L}(\theta) = \displaystyle\prod_{i=1}^{n}\frac{1}{\sqrt{2\pi}\sigma} exp\left(- \frac{(y^{i}-\theta^{T}x^{i})^{2}}{2 \sigma^{2}}\right)$$

---

## Maximum Likelihood

What is the way to choose optimal parameter $\theta$ ?
* Maximum Likelihood

Idea : choose $\theta$, such a  way to make the probability of data as high as possible

That is, optimal parameter is $$\theta^{*} = \text{arg max}_{\theta} \mathcal{L}(\theta)$$

---

## Log Likelihood

Can we find any other function to optimize for getting $\theta$ ?
* Instead of maximizing $\mathcal{L}(\theta)$
* We can maximize any increasing function of $\mathcal{L}(\theta)$
* Log Likelihood 

Why to go for any other function ?
* Simplicity of derivation

---

## Log Likelihood

Log Likelihood function is : $$l(\theta) = log \,\,\mathcal{L}(\theta) = log\displaystyle\prod_{i=1}^{n}\frac{1}{\sqrt{2\pi}\sigma} exp\left(- \frac{(y^{i}-\theta^{T}x^{i})^{2}}{2 \sigma^{2}}\right)$$

After algebraic manipulations : $$l(\theta) = n\,log\, \frac{1}{\sqrt{2 \pi}\sigma}-\frac{1}{\sigma^{2}} \frac{1}{2} \displaystyle\sum_{i =1}^{n} (y^{i}-\theta^{T}x^{i})^2$$

---

## Optimization Problem

Maximizing log likelihood $l(\theta)$ is equivalent of : $$\text{min}\,\, \frac{1}{2}\sum_{i =1}^{n} (y^{i}-\theta^{T}x^{i})^2$$

This is same as --ordinary least squares cost function-- $J(\theta)$

---

## Summary

Under the probabilistic assumptions on the data :
* Least-squares regression corresponds to finding the maximum likelihood estimate of $\theta$

Note : Probabilistic assumption of data is not necessary to justify the use of lease squares

---

