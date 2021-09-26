---
title: Generalized Linear Model
topic: Generalized Linear Model
---

## Sigmoid Function

Recall :
* Logistic function $$f(z) = \frac{1}{1+e^{-z}}$$
* $f(z) \in [0,1]$

diagram of sigmoid function

How to force Logistic function to output the values either 0 or 1 ?

---

## Perceptron

Threshold function $$g(\mathbf z) = {\begin{cases} 1 \quad\text{If}\,\, \mathbf {z} \geq 0, \\0 \quad \text{If}\,\,\mathbf z<0\end{cases}}$$

Threshold function output either 0 or 1, i.e, $g(z) \in \{0,1\}$

The hypotheses function is : $h_{\theta} (x) = g(\theta^T x)$

---

## Perceptron Learning Algorithm 

Perceptron Update Rule : $$\theta_j = \theta_j + \alpha (y^i - h_{\theta}(x^i))x_j$$

Here, $(y^i - h_{\theta}(x^i))$ takes wither 0 or $\pm$ 1

Idea is to go over one example one by one: 
* If example is classified correctly do nothing
* If example is misclassified then add or subtract the example $x_j$ to $\theta$

---

## Idea of Perceptron 

Idea :
* Want $\theta$ to be similar to $x_j$, If $y=1$
* Want $\theta$ to be not similar to $x_j$, If $y=1$

That is, we update $\theta$ in the direction of $x_j$ in case of misclassification

---

# Generalized Linear Models

---

## Introduction to Generalized Linear Models

So far, we've seen a regression example, and a classification example. In the regression example, we had $y|x;\theta \sim \mathcal{N}(\mu, \sigma^2)$ and in the classification one: $y|x;\theta \sim \text{Bernoulli}(\phi)$ for some appropriate definitions of $\mu$ and $\phi$ as functions of $x$ and $\theta$. We show, both of these methods are special cases of a broader family of models. This broader class is called Generalized Linear Models (GLM).

In this section, we will show that both of these methods are special cases of a broader family of models, called Generalized Linear Models (GLMs). We will also show how other models in the GLM family can be derived and applied to other classification and regression problems. 

To work our way up to GLMs, we will begin by defining exponential family distributions. We say that a class of distributions is in the exponential family if it can be written in the form : $$p(y;\eta) = b(y)\,\,\text{exp}(\eta^TT(y) - a(\eta)) $$

Here, $\eta$ is called natural / canonical parameter (of distribution). $T(y)$ is called sufficient statistic (for us, $T(y)= y$). $a(\eta)$ is the log partition function (for normalizing). And $b(y)$ is Base measure and $y$ is the data. The role of $e^{a(\eta))}$ essentially plays a normalizing constant that makes sure that distribution $p(y;\eta)$ sum/integrates $y$ to 1.


---

## Exponential Family

Fixed choice of $T(y), a(\eta), b(y)$ decides :
* The family of distributions that is parametrized by $\eta$
* As $\eta$ varies, We get different distributions within this family

---

## Bernoulli Distribution

Parameter $\phi$, defines the distribution over $y \in \{0,1\}$

Used for modeling the binary data

Bernoulli $(\phi)$ PDF : $$p(y;\phi) = \phi^y (1-\phi)^{(1-y)}$$

---

## Bernoulli as Exponential Family

Bernoulli PDF can be written as $$p(y;\phi) = \phi^y (1-\phi)^{(1-y)} = exp\left(log\left(\frac{\phi}{1-\phi}\right) y + log(1-\phi)\right)$$

Comparing to the form of Exponential Family : $$b(y)=1,\,\,\, \eta = log\left(\frac{\phi}{1-\phi}\right)\\ a(\eta)= -log(1-\phi) = log(1+e^\eta),\,\,\,T(y)=y$$

---

## Bernoulli as Exponential Family

Observations :
* The natural parameter of Bernoulli family $\eta = log\left(\frac{\phi}{1-\phi}\right)$
* If we solve for $\phi$, then $\phi = \frac{1}{1-e^{-\eta}}$
* This is a Logistic function

This complete the formulation of the Bernoulli distribution as an exponential family distribution

---

## Gaussian Distribution

Gaussian Distribution Parameter : mean $\mu$, and variance $\sigma^2$

We assume $\sigma^2 =1$

The PDF of Gaussian is $$p(y;\mu) = \frac{1}{\sqrt{2\pi}}\,\,exp\left(- \frac{1}{2}(y-\mu)^2\right) \\\hspace{85pt}= \frac{1}{\sqrt{2\pi}}\,\,exp\left(- \frac{1}{2}y^2\right)\,\,exp\left(\pi\mu-\frac{1}{2}\mu^2\right)$$

---

## Gaussian as Exponential Family

Comparing to the form of Exponential Family : $$\eta = \mu,\,\, a(\eta) = \frac{\mu^2}{2} = \frac{\eta^2}{2},\,\,\\ b(y) = \left(\frac{1}{\sqrt{2\pi}}\right) exp\left(-\frac{y^2}{2}\right)$$

This shows the formulation of the Gaussian distribution as an exponential family distribution

---

## Other Exponential Family Distributions

The Exponential Family Distributions :
* The Multinomial 
* The Poission (for modeling count data, i.e, $y$)
* The Gamma and Exponential (for continuos and non-negative RVs)
* The Beta and Dirichlet (for distributions over probabilities)
* Gaussian (for Real valued data)

---

## Properties of Exponential Family

MLE with respect to $\eta$ is concave

NLL (negative log likelihood) is convex

$E[y;\eta] = \frac{\partial}{\partial \eta} a(\eta)$

$Var[y;\eta] = \frac{\partial^2}{\partial^2 \eta} a(\eta)$

Note: for getting the mean and variance parameters, we need differentiation operation (not integration), which is less costly

---

## Generalized Linear Models

Natural extension of exponential family

Assumptions / Design choices :
* $y|x;\theta \sim \text{Exponential Family} (\eta)$
* $\eta = \theta^Tx, \quad \theta\in \mathbb {R}^n,\quad x\in \mathbb {R}^n$
* Test time : the output for a given $x$ or hypotheses function $h_{\theta}(x) = E[y;\eta]$

---

## Generalized Linear Models

Diagram 

Output of the model of the model (linear model) becomes $\eta$ (distribution parameter of exponential family)

During training time, we are Learning model parameter $\theta$, By $$\displaystyle \text{max}_{\theta}\,\, \text{log} p(y^i;\theta^Tx^i)$$

Since, $\eta = \theta^Tx$, During Test time, the hypotheses function is $$h_{\theta}(x) = E[y;\eta] = E[y;\theta^Tx]$$

---

## GLM training

Learning Update Rule : $$\theta_j = \theta_j + \alpha (y^i -h_{\theta}(x^i))x_j^i$$

Need to plug appropriate $h_{\theta}$ based on the distribution

Terminology :
* $\eta$ is natural parameter
* $\mu = E[y;\eta] = g(\eta)$, called canonical response function $(g(\eta)=\frac{\partial}{\partial\eta}a(\eta))$
* $\eta = g^{-1}(\mu)$, called canonical link function

---

## Parameterization

Model Parameter $(\theta)$ :
* The learnable parameter in GLMs

Natural Parameter $\eta$ :
* For Linear Models $\eta = \theta^Tx$ (Design choice)

Canonical Parameters :
* $\phi$ for Bernoulli
* $\mu, \sigma^2$ for Gaussian
* $\lambda$ for Poission
* Canonical Parameters $(\phi, \mu)$ are given by $g(\eta)$

---

## Logistic Regression

Hypotheses function $$h_{\theta}(x) = E[y|x;\theta] = \phi = \frac{1}{1+e^{-\eta}} = \frac{1}{1+e^{-\theta^Tx}}$$

Logistic function is the natural way of modeling for Binary Classification

---

## Softmax Regression



---