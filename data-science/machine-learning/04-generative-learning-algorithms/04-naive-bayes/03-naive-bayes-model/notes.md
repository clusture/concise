---
title: Naive Bayes Model
topic: Naive Bayes
slug: naive-bayes-model
---

# Naive Bayes Model

Naive bayes assumes that the features are conditionally independent of each other. This assumption is called **naive bayes assumption**. The resulting algorithm is called **naive bayes classifier**.

Recalling the text classification example, where the goal is to find whether a given email is spam or not. We represent each email with word vector whose length is equal to the total number of words in vocabulary.

With naive bayes assumption, we can model each word independently since we assume they are independent given a class. We can then model it as Bernoulli. We know this might not be true. That's why we call it naive.

Note that, we modeled it as Bernoulli as the feature vector elements will have either $0$ or $1$ depending on whether the word present in the email or not. However, the concepts discussed in the naive bayes algorithm are applicable for the case where feature $x_i$'s taking discrete values like $\{1,2,\ldots,k\}$. Here, the $p(x_i | y)$ can be modeled as multinomial distribution rather than Bernoulli.

We note that even though the Naive Bayes assumption is an extremely strong assumptions, the resulting algorithm works well on many problems. Removing naive bayes assumption requires a lot of additional calculations on dependency.

Let us say, we have total $50000$ words in vocabulary. Then, for classifying the email, we need to compute :
$$\begin{aligned}p(x_1,\ldots,x_{50000} | y) &= p(x_1|y) p(x_2|y, x_1) p(x_3|x_1,x_2,y) \ldots p(x_{50000}|y,x_1,x_2,\ldots,x_{49999})\\
&= p(x_1|y) p(x_2|y) p(x_3|y) \ldots p(x_{50000}|y) \\
&= \prod_{i=1}^{50000} p(x_i|y)\end{aligned}$$

The first equality simply follows from the usual properties of probabilities, and the second equality used the naive bayes assumption. The naive bayes assumption results in the following : 
$$p(x_i| x_j,y) = p(x_i |y),\,\, \text{where}\,\, i \ne j$$

We can parameterize the model by $\phi_{i|y=1} = p(x_i =1 | y=1)$,  $\phi_{i|y=0} = p(x_i =1 | y=0)$ and $\phi_y = p(y=1)$. Here, $y=1$ refers to class of spam emails.

How to estimate these parameters so that we can compute $p(x|y)$ which is equal to $p(x_1,\ldots,x_{50000} | y)$ for this example ?



