---
title: Naive Bayes Assumption
topic: Naive Bayes
slug: naive-bayes-assumption
---

# Naive Bayes Assumption

Naive Bayes algorithm in order to estimate $p(x|y)$ (likelihood), It assumes the strong conditional independence between the features given class. 

The conditional independence assumption where features $x_i$ are conditionally independent given $y$ is represented by :
$$p(x_1 \cap x_2 | y) = p(x_1 | y) p(x_2 | y)$$

It means that naive bayes assumes that the features are conditionally independent of each other. This assumption is called **naive bayes assumption**. Let us understand this assumption with respect to an example.

Let us take the following dataset :

|  | Outlook | Temperature | Humidity | Windy | Play Golf |
| :--: | :--: | :--: | :--: | :--: | :--: |
| 1.| Rainy | Hot | High | False | No |
| 2. | Overcast | Hot | High | False | Yes | 
| 3. | Sunny | Mild | High | True | Yes |
| | $\vdots$ |  $\vdots$| $\vdots$ | $\vdots$ | $\vdots$ |

We classify whether the day is suitable for playing golf, given the features of the day. The columns represent these features and the rows represent individual entries.

If we take the first row of the dataset, we can observe that is not suitable for playing golf if the outlook is rainy, temperature is hot, humidity is high and it is not windy.

As per naive bayes assumption, these features/predictors are conditionally independent. That is, for a given playing golf condition, If the temperature is hot, it does not necessarily mean that the humidity is high. Which need not be the case.

Another example of naive bayes assumption with respect to text classification example. What it means is that if, say, an email is known in the class of sport, the appearance of word "basketball" is independent of that of word "dunk". Which may not be true. That's why we call it naive.

Naive bayes assumption is not equivalent to assuming the features are independent. Which can be written as following. If $x_1$ and $x_2$ are two features, Then if they are independent then : 
$$p(x_1 \cap x_2) = p(x_1)\,\, p(x_2)\quad \text{Or}\quad p(x_1 | x_2) = p(x_1)$$

Another assumption naive bayes algorithm makes is that it assumes each feature has the same influence(or importance). And, none of the attributes are irrelevant and assumed to be contributing equally to the outcome.

For example, the day being windy does not have more importance in deciding to play golf or not.

