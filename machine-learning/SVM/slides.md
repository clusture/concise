---
title: Support Vector Machines
topic: Support Vector Machines
---

## Support Vector Machines (SVMs)

SVMs are among the best "off-the-shelf" supervised learning algorithms

To understand Support Vector Machines, Need to understand first :
* Margins 
* Ideal of separating the data

---

## Margins

In Logistic Regression :
* The $p(y=1|x;\theta)$ is modeled by $h_{\theta}(x) = g(\theta^Tx)$
* We predict $1$, iff $h_{\theta}(x) \geq 0.5$ Or $\theta^Tx \geq 0$
* The larger $\theta^Tx \geq 0$ is , larger $h_{\theta}(x) = p(y=1|x;\theta)$
* Thus also the higher our degree of "confidence" that the label is 1

---

## Margins

Informally we can think of our prediction as being very confident that $y=1$ if $\theta^Tx \gg 0$

Similarly, we think of logistic regression as confidently predicting $y = 0$ if $\theta^Tx \ll 0$

Given a training set again, we can find $\theta$ so that $\theta^T x^i \gg 0$ if $y^i=1$ and $\theta^T x^i \ll 0$ if $y^i = 0$

---

## Notation

Let us consider a linear classifier for a binary classification problem with labels $y$ and features $x$

We use $y \in \{-1, 1\}$ instead of $\{0,1\}$

Instead of using the $\theta$ for parameterization, we use $w,b$. Then we can write our classifier as $$h_{w,b}(x) = g(w^Tx + b)$$

Here, $g(z) = 1$ if $z \ge 0$ and $y= -1$, otherwise

Classifier directly predicts either $-1$ or $1$ without intermediate steps of estimating $p(y=1)$ etc..

---

## Functional Margin

Given training example $(x^i, y^i)$, we define the Functional margin of $(w,b)$ is given by $$\hat{\gamma}^i = y^i(w^Tx^i+b)$$

If $y^i = 1$ then for Functional margin to be large, we need $w^Tx^i+b$ to be large positive number

If $y^i = -1$ then for Functional margin to be large, we need $w^Tx^i+b$ to be large negative number

If $y^i(w^Tx^i+b) > 0$ then our prediction on this example is correct

Hence, a large functional margin represents a confident and a correct prediction

---

## Functional Margin

Given a training set $\{(x^i,y^i); i=1,\ldots,n\}$, we define the function margin of $(w,b)$ with respect to $S$ as : $$\hat{\gamma} = {\underset {i = 1,\ldots,n} {\operatorname {max}}} \hat{\gamma}^i$$

---

## Geometric Margin

Given training example $(x^i, y^i)$, we define the geometric margin of $(w,b)$ is given by $$\gamma^i = \frac{y^i(w^Tx^i+b)}{\lVert w \rVert}$$

Given a training set $\{(x^i,y^i); i=1,\ldots,n\}$, we define the geometric margin of $(w,b)$ with respect to $S$ as : $$\gamma = {\underset {i = 1,\ldots,n} {\operatorname {max}}} \gamma^i$$

---

## Optimal margin classifier

Given a training set, we want :
* To find the decision boundary that maximizes the margins
* This would reflect in a strong predictions on training set
* Results in strong classifier

How to find the separating hyperplane that achieves the maximum geometric margin : $${\begin{array}{rcll}{\underset {\gamma, w, b} {\operatorname {max}}} &~&\gamma &\\{\mathrm  {subject~to}}&~& y^i(w^Tx^i+b) \geq \gamma,\,\, i=1,\ldots,n \\&~& \lVert w \rVert = 1\end{array}}$$

---

## Optimal Margin Classifier

We want to maximize $\gamma$ subject to each training example having functional margin atleast $\gamma$

Constraint $\lVert w\rVert = 1$ ensures that functional margin equals geometric margin

However, the optimization problem is the harder one to solve

---

## Optimal Margin Classifier

We know that the geometric margin is related to function margin by $\gamma = \frac{\hat{\gamma}}{\lVert w \rVert}$

Transforming the optimization problem : $${\begin{array}{rcll}{\underset {\hat{\gamma}, w, b} {\operatorname {max}}} &~&\frac{\hat{\gamma}}{\lVert w \rVert} &\\{\mathrm  {subject~to}}&~& y^i(w^Tx^i+b) \geq \hat{\gamma},\,\, i=1,\ldots,n \end{array}}$$

---

## Optimal Margin Classifier

By substituting, $w = \frac{1}{\gamma}$ the optimization problem is given by : $${\begin{array}{rcll}{\underset { w, b} {\operatorname {max}}} &~&\frac{1}{\lVert w \rVert} &\\{\mathrm  {subject~to}}&~& y^i(w^Tx^i+b) \geq 1,\,\, i=1,\ldots,n \end{array}}$$

---

## Optimal Margin Classifier

Converting the maximization problem to a minimization problem : $${\begin{array}{rcll}{\underset {w, b} {\operatorname {min}}} &~&\frac{1}{2} \lVert w \rVert^2 &\\{\mathrm  {subject~to}}&~& y^i(w^Tx^i+b) \geq 1,\,\, i=1,\ldots,n \end{array}}$$

The above optimization problem with a convex quadratic objective and only linear constraints.

The solution of the above optimization problem gives us the optimal margin classifier

---

## Support Vector

Recall the optimization problem : $${\begin{array}{rcll}{\underset {w, b} {\operatorname {min}}} &~&\frac{1}{2} \lVert w \rVert^2 &\\{\mathrm  {subject~to}}&~& y^i(w^Tx^i+b) \geq 1,\,\, i=1,\ldots,n \end{array}}$$

diagram

The points on the dashed lines are called Support Vectors

---

## Dual form of Optimization Problem

The Lagrangian for the optimization problem is given by : $$\mathcal{L}(w,b,\alpha) = \frac{1}{2} \lVert w \rVert^2 - \sum_{i=1}^n \alpha_i (y^i(w^Tx^i+b) - 1)$$

To find the dual form of the problem : 
* Minimize with respect to $w,b$
* $\nabla_w \mathcal{L}(w,b,\alpha) =  w - \sum_{i=1}^n \alpha_i y^i x^i = 0$
* This implies $ w = \sum_{i=1}^n \alpha_i y^i x^i$
* $\frac{\partial}{\partial b} \mathcal{L}(w,b,\alpha) =  \sum_{i=1}^n \alpha_i y^i = 0$

---

## Dual form of Optimization Problem 

By substituting the definition $ w = \sum_{i=1}^n \alpha_i y^i x^i$, we get : $$\mathcal{L}(w,b,\alpha) = \sum_{i=1}^n \alpha_i - \frac{1}{2} \sum_{i,j =1}^n y^i y^j \alpha_i \alpha_j (x^i)^T x^j -b \sum_{i=1}^n \alpha_i y^i$$

This equation above by minimizing $\mathcal{L}$ with respect to $w$ and $b$

After substituting the constraints $\alpha_i \geq 0$ and $\sum_{i=1}^n \alpha_i y^i = 0$, we get the dual optimization problem: $${\begin{array}{rcll}{\underset {\alpha} {\operatorname {max}}} &~& W(\alpha) = \sum_{i=1}^n \alpha_i - \frac{1}{2} \sum_{i,j =1}^n y^i y^j \alpha_i \alpha_j < x^i ,x^j >&\\{\mathrm  {subject~to}}&~& \alpha_i \geq 0,\,\, i=1,\ldots,n \\ &~& \sum_{i=1}^n \alpha_i y^i =0 \end{array}}$$

---

## Optimal Parameters

Assuming, we know how to get optimal $\alpha$, we find the optimal $w^*$ from the equation $w = \sum_{i=1}^m \alpha_i y^i x^i$

the optimal parameter value $b^*$ is given by : $$b^* = -\frac{{\underset {i: y^i = -1} {\operatorname {max}}} (w^*)^Tx^i + {\underset {i: y^i = 1} {\operatorname {min}}} (w^*)^Tx^i}{2}$$

---

## Prediction using SVM

For a new point $x$, we can calculate $w^Tx + b$ and predict $y=1$, only if the value of quantity is more than zero

We can write $$w^Tx + b = \left(\sum_{i=1}^m \alpha_i y^i x^i\right)^Tx + b = \sum_{i=1}^m \alpha_i y^i <x^i,x> + b$$

We know that, all $\alpha_i$ will be zero except for the support vectors 

Thus, many of the terms in the sum above will be zero, and we really need to find only the inner products between $x$ and the support vectors (of which there is often only a small number) in order calculate and make our prediction.

---

## Optimal Margin Classifier

Recall the optimal parameter $w$ for the optimal margin classifier is given by : $$w = \sum_{i=1}^m \alpha_i y^i x^i$$
This can be interpreted as the linear combination of input training examples

The optimal parameter values are the linear combinations of the input features or training examples (Both in Logistic Regression and Optimal Margin Classifier)

---

## Intuition

Intuition 1: Recall the Logistic Regression
* The gradient update is given by $\theta = \theta - \alpha (h_{\theta}(x^i) - y^i) x^i$
* The batch gradient update is given by $\theta = \theta - \alpha \sum_{i=1}^m(h_{\theta}(x^i) - y^i) x^i$
* Here, the parameter theta is update by some constant times the training examples

---

## Intuition

Intuition 2:
* The vector $w$ is orthogonal to the decision boundary
* The $w$ can be thought of as a linear combination of training examples

The formal proof is given by Representor Theorem

---

## Conclusion of SVMs

By examining the dual form of the optimization problem, we gained significant insight into the structure of the problem, and were also able to write the entire algorithm in terms of only inner products between input feature vectors. In the next section, we will exploit this property to apply the kernels to our classification problem. The resulting algorithm, support vector machines, will be able to efficiently learn in very high dimensional spaces.

---





# Kernel Methods

---

## Kernel Methods

Recall in linear regression for house prediction :
* Idea is to predict the house price based on the living area
* We fit a linear function of features to training set
* What if the price is accurately represented a non linear function of features

---

## Feature Map

House Price Prediction Problem :
* What if the price $y$ can be represented as a non linear function of $x$ ?
* Let us take a example of fitting a cubic polynomial $y = \theta_3 x^3 + \theta_2 x^2 + \theta_1 x + \theta_0$


---

## Feature Map

We can see the cubic function as a linear function for different set of features

Let the feature function be: $\phi : \mathbb {R} \to \mathbb {R}^4$

The feature functions is defined as : $$\phi(x) = \left[1\,\,\, x\,\,\, x^2\,\,\, x^3\right]^T \in \mathbb{R}^4$$

The cubic function can be rewritten in $x$ as : $$\theta_3 x^3 + \theta_2 x^2 + \theta_1 x + \theta_0 = \theta^T \phi(x)$$

Shows cubic function as a linear function for different set of features

---

## Terminology for Kernel Methods

In the context of Kernel Methods :
* we call the original input values are called attributes
* Mapped input values $\phi(x)$ are called features
* The function $\phi$ is called feature map

---

## Least Mean Squares with features

Let us look the gradient descent algorithm for fitting the linear model $\theta^T\phi(x)$

Recall the gradient descent for linear model, which is  $h_{\theta}(x) = \theta^Tx$ : $$\theta = \theta + \alpha \sum_{i=1}^n (y^i - h_{\theta}(x^i))x^i \\ = \theta + \alpha \sum_{i=1}^n (y^i - \theta^T x^i)x^i $$

---

## Least Mean Squares with features

Let $\phi : \mathbb{R}^d \to \mathbb{R}^p$ be feature map that attribute $x$ to the features $\phi(x)$ in $\mathbb{R}^p$

Now goal is to function $\theta^T \phi(x)$ where the $\theta \in \mathbb{R}^p$

The new update rule is : $$\theta = \theta + \alpha \sum_{i=1}^n (y^i - \theta^T\phi(x^i))\phi(x^i)$$

Similarly, the stochastic gradient update rule becomes : $$\theta = \theta + \alpha \,\,(y^i - \theta^T\phi(x^i))\,\,\phi(x^i)$$

---

## Least Mean Squares with Kernel Trick

The gradient rules become computationally expensive for features $\phi(x)$

Example: 
* Let feature map $\phi(x)$ be the vector that contains all the monomials of $x$ with degree $\leq 3$
* The dimension of features $\phi(x)$ are in order of $d^3$
* Requires computing and storing $d^3$ vector
* Also, requires storing $\theta$ which is $d^3$ dimensional

---

## Kernel Trick

The idea is to not store the $\theta$ which is of high dimensional 

Assume $\theta = 0$ is the initialization

The main observation is that at anytime $\theta$ can be represented as a linear combination of vectors $\phi(x^1),\ldots, \phi(x^n)$

That is, assume $\theta = \sum_{i=1}^n \beta_i \phi(x^i)$ at some point in time, for some $\beta_1,\ldots,\beta_n \in \mathbb{R}$

---

## Kernel Trick

The claim is that for next round $\theta$ is still a linear combination of $\phi(x^1),\ldots, \phi(x^n)$

Let us see why ? : 
* We know that :$$\theta = \theta + \alpha \sum_{i=1}^n \,\,(y^i - \theta^T\phi(x^i))\,\,\phi(x^i)$$
* Substituting the $\theta = \sum_{i=1}^n \beta_i \phi(x^i)$, we get $$\theta = \sum_{i=1}^n \beta_i \phi(x^i)+ \alpha \sum_{i=1}^n \,\,(y^i - \theta^T\phi(x^i))\,\,\phi(x^i), \\ = \sum_{i=1}^n \left(\beta_i + \alpha \,\,(y^i - \theta^T\phi(x^i))\right )\,\,\phi(x^i)$$
* The new $\beta_i$ follows the update rule, $$\beta_i = \beta_i + \alpha \,\,(y^i - \theta^T\phi(x^i))$$

This concludes that the $\theta$ can be written as a linear combination of $\phi(x^1),\ldots, \phi(x^n)$

---

## Kernel Trick

Recall the $\beta_i$ update rule $$\beta_i = \beta_i + \alpha \,\,(y^i - \theta^T\phi(x^i))$$

Replacing the $\theta$ with $\theta = \sum_{j=1}^n \beta_j \phi(x^j)$ gives : $$\beta_i = \beta_i + \alpha \,\,\left(y^i - \sum_{j=1}^n \beta_j \phi(x^j)^T\phi(x^i)\right)$$

We rewrite $\phi(x^j)^T\phi(x^i)$ to $<\phi(x^j), \phi(x^i)>$, i.e, inner product of two features

---

## Kernel Trick

It may appear that while updating, we still need to compute the values of $<\phi(x^j), \phi(x^i)>$ for all the pairs of $i,j$

This is a costly as it may take roughly $\mathcal{O}(p)$ per operation

Two important things for the rescue are :
* Pre-compute pairwise inner product of $<\phi(x^j), \phi(x^i)>$ for all pairs of $i,j$
* For feature map $\phi$, which is monomials of degree $\le 3$ defined earlier, the inner product becomes : $$<\phi(x), \phi(z)> = 1 + <x,z> + <x,z>^2 + <x,z>^3$$ 


Therefore, to compute $<\phi(x), \phi(z)>$ we can compute $<x,z>$ with $\mathcal{O}(d)$ time plus some extra constant number of steps

---

## Kernel

The inner products between features are essential, 

Kernel corresponding to to feature map $\phi$ as function that maps $\chi \times \chi \to \mathbb{R}$ is defined as : $$K(x,z) \overset{\Delta}{=} <\phi(x), \phi(z)>$$

---

## Algorithm

Step 1: Compute $K(x^i,y^j) = <\phi(x^i), \phi(x^j)>$ for all $i.j \in \{1,\ldots,n\}$

Step 2: Loop : $$\beta_i = \beta_i + \alpha \,\,\left(y^i - \sum_{j=1}^n \beta_j K(x^i, x^j)\right)$$
* Can be written in vector notation as : $\beta = \beta + \alpha ({\vec y} - K\beta)$

---

## Prediction with Kernel Methods

Finally with the knowledge of representing the $\theta$ suffices to compute the prediction $\theta^T\phi(x)$

That is we have : $$\theta^T\phi(x) = \sum_{i=1}^n \beta_i \phi(x^i)^T \phi(x) = \sum_{i=1}^n \beta_i K(x^i, x)$$

All we need to know about the feature map $\phi(.)$ is encapsulated in Kernel function $K(.,.)$

---

## Properties of Kernel

Whole training algorithm can be written entirely in the language of the kernel without referring to the feature map $\phi$. so can the prediction of test example $x$

We need to define the Kernel function $K$ :
* Algorithm does not need explicit access to the feature map $\phi$ 
* We need to ensure the existence of feature map
* But, we do not need to explicitly be able to write $\phi$ down

---

## Kernel Functions

Does there exists a Kernel function, which ensures $K(x,z) = \phi(x)^T\phi(z)$ for all $x,z$

With Kernel functions, we can completely change from the idea of interface of selecting feature maps $\phi$ to the idea of selecting Kernel function $K$

The benefit is that, we need not compute or write down the analytical form $\phi$. We need only its existence

---

## Examples of Kernel Functions

Let $x,z \in \mathbb{R}^d$, let's first consider the kernel function $K(.,.)$ defined as : $K(x,z) = (x^Tz)^2$

We can also write this as : $$K(x,z) = \left(\sum_{i=1}^d x_i z_i\right)\left(\sum_{i=1}^d x_i z_i\right) = \sum_{i,j = 1}^d (x_ix_j)(z_iz_j)$$

That is $K(x,z) = <\phi(x), \phi(z)>$ is the kernel function

The feature map corresponding to the Kernel for three dimensional case is $$\phi(x) = {\begin{bmatrix}x_{1}x_{1}\\x_{1}x_{2}\\x_{1}x_{3}\\x_{2}x_{1}\\x_{2}x_{2}\\x_{2}x_{3}\\x_{3}x_{1}\\x_{3}x_{2}\\x_{3}x_{3}\end{bmatrix}}$$

Calculating high dimensional $\phi(x)$ requires $\mathcal{O}(d^2)$ time, where as finding $K(x,z)$ requires only $\mathcal{O}(d)$ time

---

## Examples of Kernel Functions

Another example of Kernel function is given by : $$K(x,z) = (x^Tz+c)^2 \\= \sum_{i,j = 1}^d (x_ix_j)(z_iz_j) + \sum_{i=1}^d (\sqrt{2c} x_i)(\sqrt{2c} z_i) + c^2$$

$$\phi(x) = {\begin{bmatrix}x_{1}x_{1}\\x_{1}x_{2}\\x_{1}x_{3}\\x_{2}x_{1}\\x_{2}x_{2}\\x_{2}x_{3}\\x_{3}x_{1}\\x_{3}x_{2}\\x_{3}x_{3}\\\sqrt{2c}x_{1}\\\sqrt{2c}x_{2}\\\sqrt{2c}x_{3} \\c\end{bmatrix}}$$

Kernel $K(x,z) = (x^Tz+c)^2$ correspond to feature mapping to an $\begin{bmatrix}d+k \\ d\end{bmatrix}$ feature space consists of monomials of the form $x_{i1}, x_{i2}, \ldots, x_{ik}$ that are up to order $k$

Despite working in $\mathcal{O}(d^k)$ dimensional space computing $K(x,z)$ still only takes only $\mathcal{O}(d)$

So we need not explicitly represent the feature map in very high dimensional space

---

## Kernel as Similarly Metric

We want :
* If $x,z$ are close then we want $K(x,z) = \phi(x)^T \phi(z)$ large
* If $x,z$ are far (nearly orthogonal) then we want $K(x,z) = \phi(x)^T \phi(z)$ small

We can think $K(x,z)$ as measure of how close or similar are $x,z$ Or $\phi(x), \phi(z)$

Let us consider a example of Kernel ; $$K(x,z) = \text{exp}\left(-\frac{\|x-z\|^2}{2 \sigma^2}\right)$$

If $x,z$ are similar then $K(x,z)$ will be close to 1 

Does there exists a feature ap $\phi$ such that above defined Kernel satisfies $K(x,z) = \phi(x)^T\phi(z)$ ?

The answer is Yes. This case it is called Gaussian Kernel and correspond to infinite dimensional feature mapping $\phi$ 

---

## Necessary Conditions for Valid Kernels

What properties Kernel $K$ needs to satisfy so that it can be a valid kernel function that corresponds to some feature map $\phi$

Kernel matrix is defined for the finite set of points $\{x^1, x^2, \ldots, x^n\}$. The Kernel matrix $K$ is $n \times n$ matrix. The entry $(i,j)$ of matrix is given by $K_{ij}$. The value of the entry is calculated from the Kernel function $K$. The value of the entry $K_{ij} = K(x^i, x^j)$.

Let us assume that Kernel $K$ corresponding to some feature map $\phi$. Let us look for properties that Kernel $K$ needs to satisfy :
* Then $K_{ij} = K(x^i, x^j) = \phi(x^i)^T \phi(x^j) = \phi(x^j)^T \phi(x^i) = K(x^j, x^i) = K_{ji}$
* Kernel matrix is symmetric matrix

Let $\phi_{k}(x)$ denote the $k$-th element of vector $\phi(x)$

Let $z$ be any vector then, we have $$\begin{aligned} z^T K z = \sum_i \sum_j z_i K_{ij} z_j &= \sum_i \sum_j z_i \phi(x^i)^T \phi(x^j) z_j \\&= \sum_i \sum_j z_i \sum_k \phi(x_k^i)\phi(x_k^j) z_j \\&= \sum_k \sum_i \sum_j  z_i \phi_k(x^i)\phi_k(x^j) z_j \\&= \sum_k \left( z_i \phi_k(x^i) \right)^2 \\& \geq 0\end{aligned}$$

In the second to last step, We are using the fact that $\sum_{ij} a_i a_j = \left(\sum_{i} a_i \right)^2$ for $a_i = z_i \phi_k(x^i)$.

Since $z$ can be any arbitrary vector, this shows that $K$ is positive semi-definite matrix. That is $K \geq 0$

We have shown that if $K$ is a valid Kernel then the Kernel matrix corresponding to it $K \in \mathbb{R}^{n \times n}$ is symmetric and positive semi-definite

---

## Sufficient Conditions for Valid Kernels

More generally, the condition above turns out to be not only a necessary, but also a sufficient, condition for $K$ to be a valid kernel. 

This result is due to Mercer.

Mercer Theorem : Let $K: \mathbb{R}^d \times \mathbb{R}^d \to \mathbb{R}$ be given. Then for $K$ to be valid Kernel then necessary and sufficient conditions for any $x^1, x^2, \ldots, x^n$ and $n < \infty$, then the corresponding Kernel matrix is symmetric and positive semi definite.

---

## Examples of Kernels

Let us consider a digit recognition problem, where we are trying to identify the handwritten digit (0-9) given in $16 \times 16$ pixels image. Using the Polynomial
Kernel $K(x,z) = (x^Tz)^2$ or Gaussian Kernel with support vector machines (SVM) extremely good performance had been achieved in the past.

---

## Applications of Kernel Methods

We have seen the application of kernels to linear regression. We will see the support vector machines to which kernels can be directly applied. In fact, the idea of kernels has significantly broader applicability than linear regression and SVMs.

Specifically, if you have any learning algorithm that you can write in terms of only inner products $<x,z>$ between input attributes vectors and replacing it with $K(x,z)$ where $K$ is the Kernel.

One can allow their algorithm to work efficiently in the high dimensional feature space corresponding to Kernel $K$. For instance, this kernel trick can be applied with the perceptron to derive a kernel perceptron algorithm. This idea is known as the "kernel trick".

---
