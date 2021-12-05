---
title: Naive Bayes
topic: Generative Learning Algorithms
slug: naive-bayes
---

# Naive Bayes

A Naive Bayes classifier is a probabilistic machine learning model that's used for classification task. Naive Bayes is the simple generative algorithm. The core idea of the classifier is based on the Bayes theorem.

Let us look at the Bayes theorem : 
$$p(y|x) = \frac{p(x|y)\,\, p(y)}{p(x)}$$

Here :
- $p(y|x)$ is called the posterior probability
- $p(x|y)$ is called the likelihood
- $p(y)$ is called prior probability

Naive Bayes algorithm need to estimate $p(x|y)$ (likelihood) and $p(y)$ since it is a generative learning algorithm. In order for it to estimate $p(x|y)$, it needs to make some assumptions. We will cover its assumptions after seeing a motivation example.

Let us look into motivation example, where the naive bayes algorithm is used and how it is used to for the classification problems.