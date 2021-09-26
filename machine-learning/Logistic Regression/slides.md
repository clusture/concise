---
title: Logistic Regression Model
topic: Logistic Regression
---

## Classification Problem

Classification Problem :
- Goal is to map the input variable to a target variable
- The target variable is discrete
- Learning algorithm has to output a class label

Logistic Regression is a binary classification technique

---

## Binary Classification

In binary classification :
- Target variable takes ones of the two classes
- i.e, for example $y \in \{0,1\}$
- 1 (positive class)
- 0 (negative class)
 
---

## Example

[image](email-spam-or-not_10bf2793.png, square = false)

Example (email spam detection):
- To predict whether an email is spam or not
- The input/ independent variable $x^i$ are features of email
- The target variable $y=1$ if email is spam
- The target variable $y=0$ if email is not spam


---

@flip
## Hypotheses function for Classification

Learning algorithm approximates $y$ as a function of $x$ (called Hypotheses function)

supervised-learning-hypothesis_07840892.png


Example of hypotheses functions :
- Line as a hypotheses function $y = mx + c$

hypotheses-function-example_b35b9709.png

---

## Hypotheses Function of Logistic Regression

We want output of a Logistic Regression :
- Either 0 or 1 for given input variables
- But, $h_{\theta}(x) \in [0, 1]$
- How to assign a class label ?

---

## Hypotheses Function of Logistic Regression

The Hypotheses function of logistic regression is : $$h_{\theta}(x) = g(\theta^{T}x) = \frac{1}{1 + e^{\theta^T x}}$$

Here :
- $\theta^T x = \theta_0 + \theta_1 x_1 + \ldots + \theta_d x_d$ 
- Function $g$ is called Logistic function/ Sigmoid function: $$g(z) = \frac{1}{1+e^{-z}}$$

logistic-regression_20ad4dbc.png


---

## Properties of Logistic function

Logistic function/Sigmoid function: $$g(z) = \frac{1}{1+e^{-z}}$$

The logistic function :
- Outputs the value 1 as $z \to \infty$
- Outputs the value 0 as $z \to -\infty$

The sigmoid function output lies between $[0, 1]$

---

## Properties of Sigmoid Function

The derivative of Sigmoid Function : $$g'(z) = \frac{d}{dz}\,\,\frac{1}{1+e^{-z}}$$

After some algebraic manipulations : $$g'(z) = g(z)(1-g(z))$$

---

## Logistic Regression

Recall the hypotheses function of logistic regression : $$h_{\theta}(x) = g(\theta^{T}x) = \frac{1}{1 + e^{\theta^T x}}$$

Class Label :
- if $h_{\theta}(x) \ge 0.5$ then output $y=1$ (e.g: spam email)
- if $h_{\theta}(x) < 0.5$ then output $y=0$ (e.g: not a spam email)

How to fit the parameter $\theta$ ?
- Maximum Likelihood Estimation (MLE)

---

## MLE for Logistic Regression

Let us assume :
- $p(y=1|x;\theta) = h_{\theta}(x)$
-And, $p(y=0|x;\theta) = 1- h_{\theta}(x)$

Compact form of the above expressions is : $$p(y|x;\theta)=(h_{\theta}(x))^y (1-h_{\theta}(x))^{1-y}$$

---

## Likelihood for Logistic Regression

Assuming $n$ training examples are generated independently, then Likelihood : $$\mathcal{L}(\theta) = p(y|x;\theta) = \displaystyle \prod_{i=1}^n p(y^i|x^i;\theta)$$

By substituting, Likelihood is : $$\mathcal{L}(\theta) = \displaystyle \prod_{i=1}^n (h_{\theta}(x^i))^{y^i} (1-h_{\theta}(x^i))^{1-y^{i}}$$

---

## Log Likelihood for Logistic Regression

Like in Linear Regression, Log Likelihood is given by : $$l(\theta) = log \,\,\mathcal{L}(\theta) = \displaystyle \sum_{i=1}^n y^i\,log (h_{\theta}(x^i)) + (1-y^{i}) \, log\,(1-h_{\theta}(x^i)) $$

How to maximize the likelihood ?
- Gradient Ascent algorithm
- Update Rule : $\theta := \theta + \alpha \nabla_{\theta} l(\theta)$

---

## Gradient Ascent Rule for Log Likelihood

Gradient Ascent Update Rule : $\theta := \theta + \alpha \nabla_{\theta} l(\theta)$

For Gradient: $$\frac{\partial}{\partial \theta_j} l(\theta) = \left(y \frac{1}{g(\theta^Tx)} - (1-y) \frac{1}{(1-g(\theta^T x))}\right) \frac{\partial}{\partial\theta_j} g(\theta^T x)$$

After Algebraic Manipulations : $$\frac{\partial}{\partial \theta_j} l(\theta) = (y - h_{\theta}(x))x_j$$

---

## Parameter Update Rule

Stochastic Gradient Ascent Update Rule : $$\theta_j = \theta_j + \alpha (y^i - h_{\theta}(x^i))x_j^i$$

Observations :
- Identical update rule as that of Linear Regression's LMS update rule
- But not the same algorithm
- Here, $h_\theta(x^i)$ is a non-linear function of $\theta^Tx$

---

## Summary

Let $\theta^*$ be optimal parameter for the logistic regressions hypotheses function

Step 1 : $$h_{\theta^*}(x) = g((\theta^*)^{T}x) = \frac{1}{1 + e^{(\theta^*)^{T} x}}$$

Step 2 Assign a Class Label :
- if $h_{\theta^*}(x) \ge 0.5$ then output $y=1$ (e.g: spam email)
- if $h_{\theta^*}(x) < 0.5$ then output $y=0$ (e.g: not a spam email)

---