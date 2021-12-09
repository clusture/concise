---
title: Solution for Maximum Likelihood Estimation in Naive Bayes
topic: Naive Bayes
slug: soln-max-likelihood-estimation-naive-bayes
---

# Solution for Maximum Likelihood Estimation in Naive Bayes

In the maximum likelihood estimation, the optimization problem is given by :
$${\underset {\phi_{i|y=1},\, \phi_{i|y=0},\,\phi_y}{\operatorname {max}}} \mathcal{L}(\phi_{i|y=1}, \phi_{i|y=0},\phi_y)$$

Solving the above optimization problem results in the following optimal parameters :
$$\begin{aligned} \phi_{i|y=1} &= \frac{\sum_{i=1}^m \mathcal{1} (x_j^i=1 \wedge \,y^i = 1)}{\sum_{i=1}^m \mathcal{1} (y^i = 1)}\\
\phi_{i|y=0} &= \frac{\sum_{i=1}^m \mathcal{1} (x_j^i=1 \wedge \,y^i = 0)}{\sum_{i=1}^m \mathcal{1} (y^i = 0)}\\
\phi_y &= \frac{\sum_{i=1}^m \mathcal{1} (y^i = 0)}{m}\end{aligned}$$

Here, symbol $\wedge$ means "and". The interpretation of these equations are simple as following. For example, the equation corresponding to the parameter $\phi_{i|y=1}$ indicates that "faction of spam emails that containing the word $j$".

Similarly, $\phi_{i|y=1}$ indicates that "faction of non spam emails that containing the word $j$". And equation of parameter $\phi_y$ indicates the fraction of spam emails in the dataset.

These values can be estimated from the dataset directly.
