---
title: Design matrix in Ordinary Least Squares
topic: Normal Equations for Linear Regression
slug: design-matrix-ordinary-least-squares
---

# Design matrix in Ordinary Least Squares

Given a training set $(x^1, y^1), (x_{2}, y^2), \ldots , (x^{n}, y^n)$, we can define a $n \times d$ matrix that represents a training examples. This matrix is called **design matrix**. The matrix is of the following form : $$X={\begin{pmatrix} \dots (\mathbf {x}^{1})^{\mathsf {T}}\dots\\ \dots(\mathbf {x}^{2})^{\mathsf {T}}\dots\\\vdots \\\dots(\mathbf {x}^{n})^{\mathsf {T}}\dots\end{pmatrix}}
={\begin{pmatrix}x_{11}&\cdots &x_{1p}\\x_{21}&\cdots &x_{2p}\\\vdots &\vdots &\ddots &\vdots \\x_{n1}&\cdots &x_{np}\end{pmatrix}}$$

If we include the intercept term then design matrix is a $(n+1) \times d$ matrix and it is given by : $$X ={\begin{pmatrix}1&x_{11}&\cdots &x_{1p}\\1&x_{21}&\cdots &x_{2p}\\\vdots &\vdots &\ddots &\vdots \\1&x_{n1}&\cdots &x_{np}\end{pmatrix}}$$

Let ${\vec y}$ be the $n$-dimensional vector containing all the target values from the training set : 
$${\vec y} ={\begin{pmatrix}y^{1}\\y^{2}\\\vdots \\y^{n}\end{pmatrix}}$$
