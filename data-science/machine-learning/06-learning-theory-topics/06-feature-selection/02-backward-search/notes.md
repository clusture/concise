---
title: Backward Search
topic: Feature Selection
slug: backward-search
---

# Backward Search

Let the set of features in dataset be $ \mathbb{F} = \{f_1, f_2, \ldots, f_n\}$. Let us consider the following search procedure:
1. Initialize the feature set $\mathcal{F}= \mathbb{F}$ to be empty
2. Repeat 
    * For $i = \{1,2,\ldots,n\}$ and $i \in \mathcal{F}$
        * Let $\mathcal{F}_i = \mathcal{F} - {f_i}$ (remove feature $f_i$)
        * Train the model on dataset with only features in $\mathcal{F}_i$
        * Validate the trained model on $\mathcal{F}_i$ using some cross-validation method
        * Estimate generalization error on cross-validation set
    * Let $\mathcal{F}$ be the best feature set out of $\mathcal{F}_1,\ldots, \mathcal{F}_n$ which has less generalization error in the previous step
3. Select and output the best feature subset that was evaluated during the entire search procedure

In the above algorithm, we terminate the loop in the step 2 when either $\mathcal{F} = \phi$ or the number of features in the current step ($\mathcal{F}$ at iteration $j$) reaches certain pre determined threshold.

This algorithm is known as **backward search** because it starts with the full feature set and removes one feature at a time.