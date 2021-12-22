---
title: Feature Selection
topic: Learning Theory Topics
slug: feature-selection
---

# Feature Selection

One special and important case of model selection is called feature selection. Feature selection is the process of selecting the most important features from a dataset for model construction. Feature selection techniques are used for various reasons listed below :
1. To reduce the dimensionality of the dataset.
2. To have a shorter training times
3. To simplify models for easier interpretation 

The central premise when using a feature selection technique is that the data contains some features that are either redundant or irrelevant, and can thus be removed without incurring much loss of information. Redundant and irrelevant are two distinct notions, since one relevant feature may be redundant in the presence of another relevant feature with which it is strongly correlated.

The more formal way of describing the feature selection is the following. Let us say we have a dataset with $n$ number of features $\{f_1,f_2,\ldots,f_n\}$. We want to select a subset of features that are relevant to the problem at hand. The total possible combinations of subsets are $2^n$. We need to pick one out of $2^n$ which is most relevant to the problem at hand.

The most common feature selection techniques are :
1. Forward search 
2. Backward search
3. Filter selection

Let us see these methods in detail.