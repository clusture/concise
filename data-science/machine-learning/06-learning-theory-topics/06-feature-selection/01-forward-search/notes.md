---
title: Forward Search
topic: Feature Selection
slug: forward-search
---

# Forward Search

Let the set of features in dataset be $ \mathbb{F} = \{f_1, f_2, \ldots, f_n\}$. Let us consider the following search procedure:
1. Initialize the feature set $\mathcal{F}= \phi$ to be empty
2. Repeat 
    * For $i = \{1,2,\ldots,n\}$ and $i \notin \mathcal{F}$
        * Let $\mathcal{F}_i = \mathcal{F} \cup {f_i}$
        * Train the model on dataset with only features in $\mathcal{F}_i$
        * Validate the trained model on $\mathcal{F}_i$ using some cross-validation method
        * Estimate generalization error on cross-validation set
    * Let $\mathcal{F}$ be the best feature set out of $\mathcal{F}_1,\ldots, \mathcal{F}_n$ which has less generalization error in the previous step
3. Select and output the best feature subset that was evaluated during the entire search procedure

In the above algorithm, we terminate the loop in the step 2 when either $\mathcal{F} = \{f_1,f_2,\ldots,f_n\}$ or the number of features in the current step ($\mathcal{F}$ at iteration $j$) exceeds certain pre determined threshold.

This algorithm is known as **forward search** because it starts with the empty feature set and expands it by adding one feature at a time. The forward search would take $O(n^2)$ calls to learning algorithm or model.