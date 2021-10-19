---
title: How to Compute Matrix Derivatives
topic: Normal Equations for Linear Regression
slug: compute-matrix-derivatives
---

# How to Compute Matrix Derivatives

Let us take a function $f : R^{n\times d} \to R$ mapping from $n\times d$ matrices to real numbers. Then we define the derivative of $f$ with respect to matrix $A$ is given by $$\nabla_{A} f(A) = {\begin{bmatrix}\frac{\partial f}{\partial A_{11}}&\frac{\partial f}{\partial A_{12}}&\cdots &\frac{\partial f}{\partial A_{1d}}\\\frac{\partial f}{\partial A_{21}}&\frac{\partial f}{\partial A_{22}}&\cdots &\frac{\partial f}{\partial A_{2d}}\\\vdots &\vdots &\ddots &\vdots \\\frac{\partial f}{\partial A_{n1}}&\frac{\partial f}{\partial A_{n2}}&\cdots &\frac{\partial f}{\partial A_{nd}}\end{bmatrix}}\quad \text{where}\quad \mathrm {A} ={\begin{bmatrix}A_{11}&A_{12}&\cdots &A_{1d}\\A_{21}&A_{22}&\cdots &A_{2d}\\\vdots &\vdots &\ddots &\vdots \\A_{n1}&A_{n2}&\cdots &A_{nd}\end{bmatrix}}$$

The gradient itself is an $n \times d$ matrix, whose $(i,j)$-th element is $\frac{\partial f}{\partial A_{ij}}$. For example, let us take $A = {\begin{bmatrix}A_{11}&A_{12}\\ A_{11}&A_{12}\end{bmatrix}}$ is a $2 \times 2$ matrix. And, the function $f: R^{2 \times 2} \to R$ is given by $$f(A) = \frac{1}{2} A_{11} + 4 A_{12}^2 + A_{21} * A_{22}$$

Then, for the matrix derivative of $f$ with respect to $A$, we get $$\nabla_{A} f(A) = {\begin{bmatrix} \frac{1}{2}& 8 A_{12}\\ A_{22}&A_{21}\end{bmatrix}}$$

---
