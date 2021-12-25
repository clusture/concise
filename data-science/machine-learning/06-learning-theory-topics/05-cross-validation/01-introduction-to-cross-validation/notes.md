---
title: Introduction to Cross-Validation
topic: Cross Validation
slug: cross-validation-intro
---

# Introduction to Cross-Validation

Let us assume that we are given a training set $S$. In order for the model selection from the set of models $\{\mathcal{M}_1, \mathcal{M}_2,\ldots,\mathcal{M}_n \}$ (here models could be of same type or different type), Let us first look at the following procedure and see whether it results in optimal model selection or not.
1. Train the each model $\mathcal{M}$ on $S$ to get the hypothesis $h_i$
2. pick the hypothesis with the lowest training error

The above procedure does not work. The training error is not a metric that can be used to select the best model. As, the model complexity increases, the training error also decreases. This results high variance and results in overfitting.

We want a model that generalizes well. It means it should not only perform well on the training set but also perform well on the test set. For this, we will use cross-validation techniques.

The goal of cross-validation is to test the model's ability to predict new data that was not used in estimating it, in order to flag problems like overfitting and to give an insight on how the model will generalize to an independent dataset.

At high level, Cross validation is a technique that divides the training set into few subsets, and then performs the model selection on these subset. The model selection is performed by first training the model on the training set and evaluating it on the remaining part or subset of training set. The test set is used to evaluate the final performance of the model.

Let us look at the details of cross-validation.