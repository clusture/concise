---
title: Linear Regression
topic: Linear Regression
---

## Supervised Learning

Let's start by talking about a few examples of supervised learning problems. Suppose we have a dataset giving the living areas and prices of 47 houses in some location as given below : 


| Living area (in feet) | Price (in 1000 USD) |
| :---: | :---: |
| 2104 | 400 |
| 1600 | 330 |
| 2400 | 369 |
| 1416 | 232 |
| 3000 | 540 |
| $\vdots$ | $\vdots$ |

We can plot this data in two dimensional plot and see. This will be like the following :

<img width="500" src="https://chanakya-labs.s3.ap-south-1.amazonaws.com/builds//assets/house-prediction_6a56f8e2.jpg">

Given data like this, how can we learn to predict the prices of other houses in that location, as a function of the size of their living areas? That is, given a new house's living area (in feet), we should be able to predict the price of that house.

This kind of problems can be categorized as supervised learning problems.

---

## Formal Notation for Supervised Learning

To establish notation for future use, we will use $x^i$ to denote the "input" variables (living area in this example), also called input features, and $y^i$ to denote the "output" or target variable that we are trying to predict (house price in this example). Here, superscript $i$ is not the exponential. We will explain the notation in more detail later.

A pair $(x^{i},y^{i})$ is called training example and the dataset that we will use to learn is a list of training examples ${(x^{i},y^{i}) : i = 1, \ldots , n}$ called **training set**. The superscript (example $i$), is an index into the training set.

We use $\mathcal{X}$ denote space of input variables and $\mathcal{Y}$ denote the space of output variables. In the house prediction example both input and output space is real number line, i.e, $\mathcal{X} = \mathcal{Y} = \mathbb{R}$

---

## Goal of Supervised Learning

Recall that, we started with a table or dataset consists of living area and house price. Our objective there was to predict the house price for a given house's living area.

To state supervised learning more formally, the goal here is to learn a function $h : \mathcal{X} \to \mathcal{Y}$ for a given training set, so that $h(x)$ is a good predictor for $y$ corresponds to the input example $x$. The function we are trying to learn $h$ is called a hypotheses function.

We depict this process in the figure below :

<img width="500" src="https://chanakya-labs.s3.ap-south-1.amazonaws.com/builds//assets/image-hypothesis.jpg">

---

## Types of Supervised Learning

When the target variable that we are trying to predict is continuous, such as in our housing example, we call the learning problem a **regression problem**. When $y$ can take on only a small number of discrete values (such as if, given the living area, we wanted to predict if a dwelling is a house or an apartment, say), we call it a **classification problem**.

---

## Introduction to Linear Regression

Let us consider house price prediction example. Suppose we have a dataset having the living areas, number of bed rooms and prices of houses in some location as given below : 


| Living area (in feet) | No of Bedrooms | Price (in 1000 USD) |
| :---: | :---: | :---: |
| 2104 | 3 | 400 |
| 1600 | 3 | 330 |
| 2400 | 3 | 369 |
| 1416 | 2 | 232 |
| 3000 | 2 | 540 |
| $\vdots$ | $\vdots$ | $\vdots$ |

Here, each row of the table correspond to one training example. The input  $x$'s are two-dimensional vectors in $\mathbb{R}^2$, consists of both living area and number of bedrooms. That is $x_{1}^{i}$ is the living area of the $i$-th house in the training example. And, $x_{2}^{i}$ is number of bedrooms for the same house. And $y^i$ is the actual house price corresponds to the $i$-th training example. For the first training example given in the table : $$x^1 = \begin{bmatrix}2104\\3\end{bmatrix}\text{and}\,\, y^1 = 400$$

To perform supervised learning, we must decide how we are going to represent functions/hypotheses $h$ in a computer. As an initial choice, let's say we decide to approximate $y$ as a **linear function** of $x$: $$h_{\theta}(x) = \theta_{0} + \theta_{1} x_{1} + \theta_{2} x_{2}$$

Here, the $\theta_i$'s are parameters (also called as weights) parameterizing the space of linear functions mapping from $\mathcal{X}$ to $\mathcal{Y}$. Let us look at, how to interpret this with respect to house prediction example. For a given home $x$, we calculate $h_{\theta}(x)$ and use it as a prediction for the price of house $x$.


To simplify the notation, let us introduce the convention of $x_0 = 1$ (intercept term) and also the drop the subscript $\theta$ from $h_{\theta}(x)$ for representing hypotheses function. Then our hypotheses function looks like : $$h(x) = \sum_{i=0}^d \theta_i x_i = \theta^T x$$

Here, both $\theta$ and $x$ are $d$ dimensional vectors. Hence, the parameter to learn is $\theta$, which is a $d$-dimensional vector in this model. Now, given a training set, how do we pick or learn the parameter $\theta$ ? The idea here is to make $h(x)$ as much as close to $y$, atleast for the training examples that we have.

The idea is to define the cost function that measures the distance between $h(x^i)$ and $y^i$ for each example $x^i$ in the training set for a given value of parameter $\theta$. The cost function is given by : $$J(\theta) = \frac{1}{2} \sum_{i=1}^{n} (h_{\theta}(x^{i}) - y^{i})^{2}$$

In linear regression, this cost function is called **least squares cost function**. This gives raise to **ordinary least squares** regression model. 

---

# LMS Algorithm

---

## Least Mean Squares Algorithm

We want to choose $\theta$ that minimizes $J(\theta)$. That is, our optimization problem can be formulated as: $$ \text{min}_{\theta} J(\theta)$$

In order to that, we can use the learning algorithm that starts with some initial guess for $\theta$, and that repeatedly changes $\theta$ after each iteration to make $J(\theta)$ smaller and we reach a $\theta$ that minimizes the $J(\theta)$. Let us consider gradient descent algorithm. It starts with some initial $\theta$ and repeatedly performs the following update :  $$\theta_{j} = \theta_{j} - \alpha \frac{\partial}{\partial \theta_{j}} J(\theta),\,\,\, j = 0,1,\ldots,d$$

Here, $\alpha$ is called the learning rate. This is a very natural algorithm that repeatedly takes a step in the direction of steepest decrease of $J$. The vector form of the gradient descent rule is given by : $$\theta = \theta - \alpha \nabla_{\theta} J(\theta)$$

Here, the gradient is given by  $\nabla_{\theta} J(\theta) = {\begin{bmatrix}\frac{\partial J(\theta)}{\partial \theta_{0}}\\\frac{\partial J(\theta)}{\partial \theta_{1}}\\\vdots \\\frac{\partial J(\theta)}{\partial \theta_{d}}\end{bmatrix}}$

In order to implement this algorithm, we need to figure out the partial derivative term $\frac{\partial}{\partial \theta_{j}}$ on the right hand size. For now, let us assume that, we have only one training example $(x,y)$, then we have : $$\begin{aligned}\frac{\partial}{\partial \theta_{j}} &= \frac{\partial}{\partial \theta_{j}} \frac{1}{2} (h_{\theta}(x) - y)^{2} \\ &= 2 . \frac{1}{2} (h_{\theta}(x) - y)\frac{\partial}{\partial \theta_{j}} (h_{\theta}(x) - y)\\ &= (h_{\theta}(x) - y)\frac{\partial}{\partial \theta_{j}} \left(\sum_{i=0}^d \theta_i x_i - y \right)\\ &= (h_{\theta}(x) - y) x_j \end{aligned}$$

Here, we used the fact that $h_{\theta}(x) = \sum_{i=0}^d \theta_i x_i$. For the single training example, the gradient descent update rule is given by : $$\theta_{j} = \theta_{j} + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i}$$

This rule is called LMS update rule. LMS stands for least mean squares. We can make the following observations regarding the update rule. The magnitude of parameter $\theta$ update is directly proportional to error $(y^{i} - h_{\theta}(x^{i}))$. Closer the prediction, small is the update to current parameter. 

So far, we have looked the case where training set has only one example. Let us looks for the ways to generalize the update rule for the cases where training set having more than one training example. One way to modify the update rule to work with more than one training example is the following 

$$\begin{aligned}
&\text{repeat until convergence}\,\, \{ \\
&\theta_{j} = \theta_{j} + \alpha \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^{i})) x_{j}^{i},\,\, \text{(for every j)} \\
&\}
\end{aligned}
$$

We can write the above algorithm in vector form as following : $$\theta = \theta + \alpha \sum_{i=1}^{n} (y^{i} - h_{\theta}(x^i)) x^{i}$$

This method looks at each and every training example on the training set for every step and computes the gradient and updates the parameter $\theta$. This update rule is called **batch gradient descent**. Gradient descent can be suspectable to local minima in general. However, the optimization problem that we have formulated here has one global minima and no local minima. Thus, gradient descent always converges to local minima. 

There are alternatives to batch gradient descent. Consider the following iterative algorithm : 
$$\begin{aligned}
&\text{Loop}\,\, \{ \\
&\text{for i= 1 to n, }\,\, \{ \\
&\theta_{j} = \theta_{j} + \alpha (y^{i} - h_{\theta}(x^{i})) x_{j}^{i},\,\, \text{(for every j)} \\
&\}
&\}
\end{aligned}
$$

By grouping the updates of coordinates into update of the vector $\theta$, we can rewrite the above rule into : $$\theta = \theta + \alpha (y^{i} - h_{\theta}(x^{i})) x^{i}$$


In this algorithm, we repeatedly run through the training set, and each time we encounter a training example, we update the parameters according to the gradient of the error with respect to that single training example only. This algorithm is called stochastic gradient descent (also incremental gradient descent). Whereas batch gradient descent has to scan through the entire training set before taking a single step, which is a costly operation if $n$ is large stochastic gradient descent can start making progress right away, and continues to make progress with each example it looks at. Often, stochastic gradient gets close to the optimal parameter $\theta$, much faster than the batch gradient descent. However, it may not converge to optimal parameter ever Or it might keep oscillating around the minimum of $J(\theta)$. But, for most of the practical uses the solution that is near to the minimum also serves as a good approximate to the true minimum. ) For these reasons, particularly when
the training set is large, stochastic gradient descent is often preferred over batch gradient descent.

---

# The Normal Equations


Gradient descent gives one way of minimizing $J$. Let's discuss a second way of doing so, this time performing the minimization explicitly and without resorting to an iterative algorithm. In this method, we will minimize $J$ by explicitly taking its derivatives with respect to the $\theta_j$'s, and setting them to zero. To enable us to do this without having to write reams of algebra and pages full of matrices of derivatives, let's introduce some notation for doing calculus with matrices.

---

## Matrix Derivatives

Let us take a function $ f : R^{n \times d} \to R$ mapping from $n \times d$ matrices to real numbers. Then we define the derivative of $f$ with respect to matrix $A$ is given by $$\nabla_{A} f(A) = {\begin{bmatrix}\frac{\partial f}{\partial A_{11}}&\frac{\partial f}{\partial A_{12}}&\cdots &\frac{\partial f}{\partial A_{1d}}\\\frac{\partial f}{\partial A_{21}}&\frac{\partial f}{\partial A_{22}}&\cdots &\frac{\partial f}{\partial A_{2d}}\\\vdots &\vdots &\ddots &\vdots \\\frac{\partial f}{\partial A_{n1}}&\frac{\partial f}{\partial A_{n2}}&\cdots &\frac{\partial f}{\partial A_{nd}}\end{bmatrix}}\quad \text{where}\quad \mathrm {A} ={\begin{bmatrix}A_{11}&A_{12}&\cdots &A_{1d}\\A_{21}&A_{22}&\cdots &A_{2d}\\\vdots &\vdots &\ddots &\vdots \\A_{n1}&A_{n2}&\cdots &A_{nd}\end{bmatrix}}$$

The gradient itself is an $n \times d$ matrix, whose $(i,j)$-th element is $\frac{\partial f}{\partial A_{ij}}$. For example, let us take $A = {\begin{bmatrix}A_{11}&A_{12}\\ A_{11}&A_{12}\end{bmatrix}}$ is a $2 \times 2$ matrix. And, the function $f: R^{2 \times 2} \to R$ is given by $$f(A) = \frac{1}{2} A_{11} + 4 A_{12}^2 + A_{21} * A_{22}$$

Then, for the matrix derivative of $f$ with respect to $A$, we get $$\nabla_{A} f(A) = {\begin{bmatrix} \frac{1}{2}& 8 A_{12}\\ A_{22}&A_{21}\end{bmatrix}}$$

---

## Ordinary Least Squares ( Revisited with Matrix Notation )

Given a training set $(x^1, y^1), (x_{2}, y^2), \ldots , (x^{n}, y^n)$, we can define a $n \times d$ matrix that represents a training examples. This matrix is called **design matrix**. The matrix is of the following form : $ X={\begin{pmatrix} \dots (\mathbf {x}^{1})^{\mathsf {T}}\dots\\ \dots(\mathbf {x}^{2})^{\mathsf {T}}\dots\\\vdots \\\dots(\mathbf {x}^{n})^{\mathsf {T}}\dots\end{pmatrix}}
={\begin{pmatrix}x_{11}&\cdots &x_{1p}\\x_{21}&\cdots &x_{2p}\\\vdots &\vdots &\ddots &\vdots \\x_{n1}&\cdots &x_{np}\end{pmatrix}} $

If we include the intercept term then design matrix is a $(n+1) \times d$ matrix and it is given by : $$X ={\begin{pmatrix}1&x_{11}&\cdots &x_{1p}\\1&x_{21}&\cdots &x_{2p}\\\vdots &\vdots &\ddots &\vdots \\1&x_{n1}&\cdots &x_{np}\end{pmatrix}}$$

Let ${\vec y}$ be the $n$-dimensional vector containing all the target values from the training set : 
$${\vec y} ={\begin{pmatrix}y^{1}\\y^{2}\\\vdots \\y^{n}\end{pmatrix}}$$

Let us recall the linear regression hypothesis function : $$h_{\theta}(x) = \sum_{j=1}^{d} \theta_{j}x_{j} = x^{T}\theta = \theta^T x, \quad \text{predicted target variable}$$

For a linear regression's hypothesis function, we can verify that : $$ \begin{aligned} X\theta - {\vec y} &= {\begin{pmatrix}  (\mathbf {x}^{1})^{\mathsf {T}}\theta\\ (\mathbf {x}^{2})^{\mathsf {T}}\theta\\\vdots \\(\mathbf {x}^{n})^{\mathsf {T}}\theta\end{pmatrix}} - {\begin{pmatrix}y^{1}\\y^{2}\\\vdots \\y^{n}\end{pmatrix}} \\&= {\begin{pmatrix}  \mathbf {h_{\theta}(x^{1}) - y^{1}}\\ \mathbf {h_{\theta}(x^{2}) - y^{2}}\\\vdots \\\mathbf {h_{\theta}(x^{n}) - y^{n}}\end{pmatrix}} \end{aligned}$$

We know that for a vector $z$, the inner product with itself is given by : $z^{T}z = \sum_{i}z_{i}^2$. Now using the matrix notations and derivations we have seen so far, we will represent the least squares regression cost function with them. 

Least Squares Cost Function for Linear Regression : $$\begin{aligned} \frac{1}{2} (X\theta - {\vec y})^{T}(X\theta - {\vec y}) &= \frac{1}{2} \sum_{t}^{n} (\mathbf {h_{\theta}(x^{i}) - y^{i}})^{2} \\ &= J(\theta) \end{aligned}$$

Recall that, we use gradient descent algorithm for finding the optimal parameter $\theta$ which minimize the cost function $J(\theta)$. The gradient of least squares cost function $J(\theta)$ is given by $$\begin{aligned}\nabla_{\theta} J(\theta) &= \nabla_{\theta}\frac{1}{2} (X\theta - {\vec y})^{T}(X\theta - {\vec y}) \\ &= X^{T}X \theta - X^{T}y\end{aligned}$$

In order to minimize $J(\theta)$, we need to set the derivative of it zero and solve for it. In our case, this translates in to **Normal equations** : $$X^{T}X \theta - X^{T}{\vec y} = 0$$

Once, we solve for parameter the value that minimizes $J(\theta)$ is given in closed form by the equation : $$\theta^{*} = (X^{T}X)^{-1}X^{T}{\vec y}$$

The final ordinary least squares or linear least squares regression model is then given by $$h(x) = \theta^* x$$

We can learn the optimal parameter for least squares regression directly through the closed form expression. 

---

## Probabilistic Interpretation of Linear Regression

When faced with a regression problem, why might linear regression, and specifically why might the least squares cost function $J$, be a reasonable choice ? In this section, we will give a set of probabilistic assumptions, under which least-squares regression is derived as a very natural algorithm. Let us assume that the target variables and the inputs are related via the equation $$y^i = \theta^T x^i + \epsilon$$

Here, $\epsilon$ refer to the error term. It captures the unmodeled effects such as missing features that are very pertinent to predicting house price Or some random noise. Let us assume that the $\epsilon^i$'s are distributed I.I.D according to a Gaussian distribution with mean zero and some variance $\sigma^2$. We can write this as $\epsilon^i \sim \mathcal{N}(0, \sigma^2)$. The density function of $\epsilon^i$ is given by $$Pr(\epsilon^{i}) = \frac{1}{\sqrt{2\pi}\sigma} -exp\left(\frac{(\epsilon^{i})^{2}}{2 \sigma^{2}}\right)$$

This implies that the conditional probability density function of $y^i$ given $x^i$ is given by : $$p(y^{i}|x^{i}; \theta) = \frac{1}{\sqrt{2\pi}\sigma} exp\left(- \frac{(y^{i}-\theta^{T}x^{i})^{2}}{2 \sigma^{2}}\right)$$

The notation $p(y^i|x^i;\theta)$ indicates that this is the distribution of $y^i$ given $x^i$ and parameter $\theta$. Note that $\theta$ is not a random variable. So, we should not condition on it. In other words, we can also write that the probability distribution of $y^i$ as $$ y^{i} | x^{i}; \theta \sim \mathcal{N}(\theta^{T}x^{i}, \sigma^{2})$$

Given design matrix $X$ and $\theta$, what is the distribution of $y^i$'s ? The probability of data is given by $p({\vec y}|X;\theta)$. This quantity can be viewed as a function of $y$ and $X$ for a fixed $\theta$. When we wish to explicitly view this as a function of $\theta$, we will instead call it the **likelihood** function : $$\mathcal{L}(\theta) = \mathcal{L}(\theta; X, {\vec y})$$

With the independence assumption of on the $\epsilon^i$'s (hence $y^i$'s given $x^i$'s), this can be also written as : $$\mathcal{L}(\theta) = p(y | X; \theta) = \prod_{i=1}^{n} p(y^{i} | x^{i}; \theta)$$ 

Given this probabilistic model relating the $y^i$'s and $x^i$'s, what is the reasonable way of choosing our best guess of parameter $\theta$ ? The principal of maximum likelihood says that we should choose $\theta$ so as to make the data as high probability as possible. I.e., we should choose $\theta$ to maximize $\mathcal{L}(\theta)$. Instead of maximizing $\mathcal{L}(\theta)$, we can also maximize any strictly increasing function of $\mathcal{L}(\theta)$. In particular, the derivations will be a bit simpler if we instead maximize the log likelihood $l(\theta)$ given by : $$\begin{aligned} l(\theta) &= \text{log} \,\,\mathcal{L}(\theta) \\&= \text{log} \prod_{i=1}^{n}\frac{1}{\sqrt{2\pi}\sigma} \text{exp}\left(- \frac{(y^{i}-\theta^{T}x^{i})^{2}}{2 \sigma^{2}}\right) \\&= \sum_{i=1}^{n} \text{log} \frac{1}{\sqrt{2\pi}\sigma} \text{exp}\left(- \frac{(y^{i}-\theta^{T}x^{i})^{2}}{2 \sigma^{2}}\right) \\&= n\,log\, \frac{1}{\sqrt{2 \pi}\sigma}-\frac{1}{\sigma^{2}} \frac{1}{2} \sum_{i =1}^{n} (y^{i}-\theta^{T}x^{i})^2\end{aligned}$$

Hence, maximizing log likelihood $l(\theta)$ gives the same answer as the minimizing : $$\text{min}\,\, \frac{1}{2}\sum_{i =1}^{n} (y^{i}-\theta^{T}x^{i})^2$$

This is same as --ordinary least squares cost function-- $J(\theta)$. To summarize: Under the previous probabilistic assumptions on the data, least-squares regression corresponds to finding the maximum likelihood estimate of $\theta$. This is thus one set of assumptions under which least-squares regression can be justified as a very natural method that's just doing maximum likelihood estimation. (Note however that the probabilistic assumptions are by no means necessary for least-squares to be a perfectly good and rational procedure, and there may—and indeed there are—other natural assumptions that can also be used to justify it.)

Note also that, in our previous discussion, our final choice of $\theta$ did not depend on what was $\sigma^2$, and indeed we'd have arrived at the same result even if $\sigma^2$ were unknown. This is used in exponential family and generalized linear models.

---

## Summary

Under the probabilistic assumptions on the data :
* Least-squares regression corresponds to finding the maximum likelihood estimate of $\theta$

Note : Probabilistic assumption of data is not necessary to justify the use of lease squares

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


