---
title: Supervised Learning for Linear Regression
topic: Introduction to Linear Regression
slug: supervised-learning
---

# Supervised Learning for Linear Regression

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

The goal of the supervised learning framework is use this dataset to learn a function that approximates the price of a house given living area and no.of bedrooms. We can use this approximate function to predict the price of a new houses.
