---
title: Problem with Naive Bayes
topic: Laplace Smoothing
slug: problem-naive-bayes
---

# Problem with Naive Bayes

The Naive Bayes algorithm  may fail to work well if a new word which does not appear in the training set comes in a email. Let us discuss what will happen if the new word appears in email. 

Suppose, the new word is $j$ th word in the dictionary, then then, Naive Bayes spam filter therefore had picked its maximum likelihood estimates of the parameters $\phi_{j|y}$ to be : 
$$\begin{aligned}\phi_{j|y=1} &= \frac{\sum_{i=1}^m \mathcal{1} \{x_j^i = 1\, \wedge \, y^i =1\}}{\sum_{i=1}^m \mathcal{1} \{y^i =1\}} = 0 \\
\phi_{j|y=0} &= \frac{\sum_{i=1}^m \mathcal{1} \{x_j^i = 1\, \wedge \, y^i =0\}}{\sum_{i=1}^m \mathcal{1} \{y^i =0\}} = 0\end{aligned}$$

That is because it has never seen word $j$ before in either spam or non-spam training examples, it thinks the probability of seeing it in either type of email is zero.

Hence, when trying to decide if one of these messages containing $j$ is spam, it calculates the class posterior probabilities, and obtains :
$$\begin{aligned} p(y=1 | x) &= \frac{ \left[\prod_{i=1}^m p(x^i|y=1)\right] p(y=1)}{\left[\prod_{i=1}^m p(x^i|y=1)\right] p(y=1) + \left[\prod_{i=1}^m p(x^i|y=0)\right] p(y=0)}\\ &= \frac{0}{0}\end{aligned}$$

This is due to terms "$\prod_{i=1}^m p(x^i|y)$" includes the term $p(x^j|y)$  that is multiplied into it. Here, we know that $p(x^j|y) =0$, where $x^j$ is a new word. Hence, Naive Bayes algorithm obtains $\frac{0}{0}$, does not know how to make the classification.

