---
title: Laplace Smoothing Technique for Naive Bayes
topic: Laplace Smoothing
slug: laplace-smoothing-technique-naive-bayes
---

# Laplace Smoothing Technique for Naive Bayes

Laplace smoothing solution for naive bayes classifier sets the optimal parameter values as following :
$$\begin{aligned} \phi_{i|y=1} &= \frac{\sum_{i=1}^m \mathcal{1} (x_j^i=1 \wedge \,y^i = 1) \,+\, 1}{\sum_{i=1}^m \mathcal{1} (y^i = 1) \,+\, 2}\\
\phi_{i|y=0} &= \frac{\sum_{i=1}^m \mathcal{1} (x_j^i=1 \wedge \,y^i = 0) \,+\, 1}{\sum_{i=1}^m \mathcal{1} (y^i = 0)\,+\, 2}\\
\phi_y &= \frac{\sum_{i=1}^m \mathcal{1} (y^i = 1) \,+\, 1}{m \,+\, k}\end{aligned}$$

Here $k$ is the number of classes. Let us understand what we did, we added $1$ in the numerator for all the parameters. And for $\phi_y$, we added $k$ in the denominator, where as for the rest of parameters we added $2$ in the denominator.

It will help in avoiding $\frac{0}{0}$ while estimating $p(y=1 | x)$ and $p(y=0 | x)$. That is "$\prod_{i=1}^m p(x^i|y)$" will be non zero as the term  $p(x^j|y) \ne0$ for $x^j$ a new word. Hence, Naive Bayes algorithm can make the classification.

In reality, the Laplace smoothing does not make too much difference since it usually has all the words but it is good to have it especially in text classification problems.