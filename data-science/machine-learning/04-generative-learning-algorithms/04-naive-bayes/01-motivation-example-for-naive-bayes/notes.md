---
title: Motivating Example for Naive Bayes
topic: Naive Bayes
slug: motivating-example-naive-bayes
---

# Motivating Example for Naive Bayes

Let us use email spam filter system as motivating example. Here, we want to classify the emails as spam or not. Based on this, those spam emails can be kept aside in separate folder. The email spam detection system application falls under one set of broader application called text classification.

![Email-Spam-Detection](./images/email-spam-detection-nb.png)

In the text classification, the given text is classified based on the words in it. Here, first step is to construct a word vector. For example, in the case of email spam detection example the word vector is used to represent the given email. Let us see how to construct a word vector.

The example of a word vector is given as : 
$$ x = \begin{pmatrix} 1\\0\\0\\\vdots\\0\\\vdots\\1\\0\end{pmatrix} \text{corresponding to} \begin{pmatrix} a\\\text{ahaha}\\\text{apple}\\\vdots\\\text{box}\\\vdots\\\text{buy}\\\text{cat}\end{pmatrix}$$

Here, the $x_i = 1$ if the word corresponding to that is present in the email, otherwise we set $x_i = 0$. For example, in the above example email has word "buy" in it, hence the word vector has value $1$ corresponding to it. 

The length of vector is the total number of words in the dataset dictionary. Set of all different words in the dataset constitute the dataset dictionary known as vocabulary.

For example, the dataset has 50,000 unique words then the size of the vocabulary is $50K$. And, the input to the classifier is the word vector $x \in \{0,1\}^{50,000}$. And the classifier needs to predict whether email is spam or not. 

In order to build a generative model, we need to estimate $p(x|y)$ and $p(y)$. To estimate, we need to assume some model for $p(x|y)$. Let us look, what assumptions naive bayes algorithm makes and how it estimates the $p(x|y)$.