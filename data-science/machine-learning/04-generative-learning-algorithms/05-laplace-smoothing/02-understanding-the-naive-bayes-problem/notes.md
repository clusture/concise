---
title: Understanding the Naive Bayes
topic: Laplace Smoothing
slug: understanding-naive-bayes
---

# Understanding the Naive Bayes

We have seen that Naive Bayes algorithm does not know how to make the classification when the new word appears in email. Let us understand the problem more broadly. 

It is statistically a bad idea to estimate the probability of some event to be zero just because you haven't seen it before in your finite training set.

There could be high chance that Naive Bayes predicts one class (could be spam or non spam) with high probability If not for the presence of new word in the email.

We cannot afford the spam filter algorithm to not classify in the real world applications. It has to decide one class.

Let us see how we can overcome this problem by simple solution called Laplace Smoothing.

