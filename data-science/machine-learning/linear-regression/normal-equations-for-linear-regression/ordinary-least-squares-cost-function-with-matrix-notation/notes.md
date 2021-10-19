---
title: Ordinary Least Squares Cost Function with Matrix Notation
topic: Normal Equations for Linear Regression
slug: ordinary-least-squares-cost-func-matrix-notation
---

# Ordinary Least Squares Cost Function with Matrix Notation

Now, since the prediction of training example $x^i$ is given by $h_{\theta}(x^i) = (x^i)^T\theta$, we can verify that : $$ \begin{aligned} X\theta - {\vec y} &= {\begin{pmatrix}  (\mathbf {x}^{1})^{\mathsf {T}}\theta\\ (\mathbf {x}^{2})^{\mathsf {T}}\theta\\\vdots \\(\mathbf {x}^{n})^{\mathsf {T}}\theta\end{pmatrix}} - {\begin{pmatrix}y^{1}\\y^{2}\\\vdots \\y^{n}\end{pmatrix}} \\&= {\begin{pmatrix}  \mathbf {h_{\theta}(x^{1}) - y^{1}}\\ \mathbf {h_{\theta}(x^{2}) - y^{2}}\\\vdots \\\mathbf {h_{\theta}(x^{n}) - y^{n}}\end{pmatrix}} \end{aligned}$$

We know that for a vector $z$, the inner product with itself is given by : $z^{T}z = \sum_{i}z_{i}^2$. Now using the matrix notations and derivations we have seen so far, we will represent the least squares regression cost function with them. 

Least Squares Cost Function for Linear Regression : $$\begin{aligned} \frac{1}{2} (X\theta - {\vec y})^{T}(X\theta - {\vec y}) &= \frac{1}{2} \sum_{t}^{n} (\mathbf {h_{\theta}(x^{i}) - y^{i}})^{2} \\ &= J(\theta) \end{aligned}$$

---
