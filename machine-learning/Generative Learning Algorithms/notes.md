---
title: Generative Learning Algorithms
topic: Generative Learning Algorithms
---

## Different Approaches to Classification

Two main approaches for Classification :
- The Generative approach and 
- The Discriminative approach

Idea of Generative approach is :
* Instead of looking at the all classes at a time, and figuring out how to separate them. Generative Learning Algorithms looks each of the classes separately in isolation.

---

## Discriminative Learning Algorithm

Discriminative Learning Algorithm :
* Learns $p(y|x)$ directly
* i.e, directly learns hypotheses function
* Example : for Binary classification $$h_{\theta}(x) = \begin{cases} 0 \quad\text{If condition} \\ 1 \quad\text{otherwise} \end{cases}$$

---

## Generative Learning Algorithms

Generative Algorithm :
* Learns $p(x|y)$
* And, Class Prior $p(y)$

Uses Bayes Rule to compute $p(y|x)$, given by $$p(y|x) = \frac{p(x|y) p(y)}{p(x)}$$

---

## Binary Classification

Example : Tumor Classification

Generative Algorithms Learn : $p(y)$ and $p(x|y)$

Using a Bayes rule, Generative Learning Algorithm computes :
* $p(y=1|x) = \frac{p(x|y=1)p(y=1)}{p(x)}$
* Since, $p(x) = p(x|y=1)p(y=1) + p(x|y=0)p(y=0)$

---

## Gaussian Discriminant Analysis

Gaussian Discriminant Analysis(GDA) is useful :
* For a classification problems
* And, If input features are continuous random variables

GDA is Generative Learning Algorithm

GDA Models $p(x|y)$ using multivariate normal distribution

---

## GDA Model

The GDA model is : $$y \sim \text{Bernoulli}(\phi),\\ x|y=0 \sim \mathcal{N}(\mu_o, \Sigma),\\ x|y=1 \sim \mathcal{N}(\mu_1, \Sigma)$$

The parameters of the model are : $\phi, \mu_0, \mu_1, \Sigma$

And, the parameters : $\phi \in [0,1], \mu_0 \in \mathcal{R}^d, \mu_1 \in \mathcal{R}^d, \Sigma \in \mathcal{R}^{d\times d}$

We have same covariance matrix $\Sigma$, though there are two different mean vectors $\mu_0, \mu_1$

---

## GDA Model

The actual distributions are : $$p(y) = y^{\phi}(1-y)^{1-\phi}, \\p(x|y=0) = \frac{1}{(2\pi)^{\frac{d}{2}}|\Sigma|^{\frac{1}{2}}} \text{exp}(-\frac{1}{2}(x-\mu_0)^T \Sigma^{-1}(x-\mu_0)), \\p(x|y=1) = \frac{1}{(2\pi)^{\frac{d}{2}}|\Sigma|^{\frac{1}{2}}} \text{exp}(-\frac{1}{2}(x-\mu_1)^T \Sigma^{-1}(x-\mu_1))$$


---

## GDA Log-Likelihood

Let the training set consists of $n$ examples of $(x^i, y^i)$

The log-likelihood function of the data is given by : $$l(\phi, \mu_0, \mu_1, \Sigma) = log \prod_{i=1}^n p(x^i, y^i; \phi, \mu_0, \mu_1, \Sigma) \\ \hspace{100pt}= log \prod_{i=1}^n\,\,  p(x^i| y^i; \phi, \mu_0, \mu_1, \Sigma)\,\,\, p(y^i; \phi)$$

Here, the cost function is the function of $x, y$

---

## Maximum likelihood estimation

The maximum likelihood estimation is given by : $${\underset {\phi, \mu_0, \mu_1, \Sigma }{\operatorname {max} }} l(\phi, \mu_0, \mu_1, \Sigma) = {\underset {\phi, \mu_0, \mu_1, \Sigma }{\operatorname {max} }} log \prod_{i=1}^n\,\,  p(x^i| y^i; \phi, \mu_0, \mu_1, \Sigma)\,\,\, p(y^i; \phi)$$

Optimize for the parameters for which the log likelihood is maximum

---

## Optimal GDA parameters

The optimal GDA parameters by solving log likelihood is given by : $$\phi = \frac{1}{n}\sum_{i=1}^{n} \mathbf{1}\{y^i = 1\}, \\ \mu_0 = \frac{\sum_{i=1}^{n}\mathbf{1}\{y^i = 0\} x^i}{\sum_{i=1}^{n}\mathbf{1}\{y^i = 0\}}, \\ \mu_0 = \frac{\sum_{i=1}^{n}\mathbf{1}\{y^i = 0\} x^i}{\sum_{i=1}^{n}\mathbf{1}\{y^i = 0\}}, \\ \Sigma = \frac{1}{n} \sum_{i=1}^{n} (x^i - \mu_{y^i}) (x^i - \mu_{y^i})^T$$

---

## How GDA works

diagram

For Binary Classification :
* GDA is fitting Gaussian distributions for each of the classes
* Decision Boundary for separating the classes

---

## Relationship between GDA and Logistic Regression

If the $p(y=1|x ;\phi, \Sigma, \mu_0, \mu_1)$ is viewed as a function of x, then : $$p(y=1|x ;\phi, \Sigma, \mu_0, \mu_1) = \frac{1}{1+exp(\theta^Tx)}$$

Here, $\theta$ is a function of $\phi, \Sigma, \mu_0, \mu_1$

This function is looks exactly like Logistic function (Discriminative Algorithm)

---

## Results / Conclusions of GDA

If $p(x|y)$ is multivariate Gaussian (with shared $\Sigma$) then $p(y|x)$ follows Logistic function

Converse is not True ($p(y|x)$ being a logistic function does not imply $p(x|y$) is
multivariate gaussian)

Hence, GDA makes stronger modeling assumptions about the data than does logistic regression.

---

## Preference for GDA Vs Logistic Regression

When these modeling assumptions are correct, then GDA will find better fits
to the data

Logistic regression is also more robust and less sensitive to incorrect modeling assumptions

Different set of assumptions leading to Logistic function is :
* If $x |y=1$ and $x|y=0$ are Poisson

---

## Naive Bayes

In Gaussian Discriminant Analysis :
* Features are continuous
* What if the feature vectors are discrete ?

Naive Bayes Algorithm can be used :
* For classification
* And when the feature are discrete

---

## Motivation Example

Email Spam Filter : 
* Classify whether email is spam or not spam
* One example of text classification

Once we have training set :
* Will have emails and corresponding class (spam or non spam)
* We begin construction of classifier by identifying the features $x_j$

---

## Feature Representation

Represent an email Via a feature vector :
* Whose length is equal to the number of words in the dictionary
* If email has $j$ th word, then $x_j = 1$ in 

The set of words encoded into feature vector is called vocabulary

---

## Example

Example:
* If we have 50000 words in the vocabulary
* Need 50000 length vector to represent a single email
* Email can be represented by one of the element $x \in \{0,1\}^{50000}$

---

## Building the Model

After choosing feature vector:
* Need to build Generative Model
* Model $p(x|y)$ and $p(y)$

To model $x$ explicitly with a multinomial distribution over the $2^{50000}$ possible outcomes, then we'd end up with a $(2^{50000}−1)$ dimensional parameter vector.

---

## How to model $p(x|y)$ ?

Make strong assumptions about features :
* $x_i$'s are conditionally independent given $y$

This assumption is called **Naive Bayes(NB) Assumption**

The resultant Generative Algorithm is called **Naive Bayes Algorithm**

---

## Naive Bayes

Now let us look, resultant of conditional independence assumption : $$p(x_1,\ldots,x_{50000}|y) = p(x_1|y)p(x_2|x_1,y)p(x_3|x_2,x_1,y)\ldots p(x_{50000}|y,x_1,\ldots,x_{49999})\\ = p(x_1|y)p(x_2|y)p(x_3|y)\ldots p(x_{50000}|y) \\ = \prod_{j=1}^{d} p(x_j|y)$$

Though, Naive Bayes assumption is an extremely strong assumptions, the resulting algorithm works well on many problems

---

## Parameters of Naive Bayes

The parameters of Naive Bayes are :
* $\phi_{j|y=1} = p(x_j=1|y=1)$
* $\phi_{j|y=0} = p(x_j=1|y=0)$
* $\phi_y = p(y=1)$

For a given training set the likelihood is given by : $$\mathcal{L}(\phi_y, \phi_{j|y=1}, \phi_{j|y=1}) = \prod_{i=1}^{n} p(x^i, y^i)$$


---

## Maximum Likelihood Estimates

Maximizing the likelihood with respect to $\phi_y, \phi_{j|y=0}, \phi_{j|y=1}$ : $${\underset {\phi_y, \phi_{j|y=0}, \phi_{j|y=1}} {\operatorname {max}} } \prod_{i=1}^{n} p(x^i, y^i)$$

The optimal parameters are : $$\phi_y = \frac{1}{n}\sum_{i=1}^{n} \mathbf{1}\{y^i = 1\}, \\ \phi_{j|y=0} = \frac{\sum_{i=1}^{n}\mathbf{1}\{x_j^i = 1\wedge y^i = 0\} }{\sum_{i=1}^{n}\mathbf{1}\{y^i = 0\}}, \\ \phi_{j|y=1} = \frac{\sum_{i=1}^{n}\mathbf{1}\{x_j^i = 1\wedge y^i = 1\} }{\sum_{i=1}^{n}\mathbf{1}\{y^i = 1\}}$$

---

## Parameters interpretation

$\phi_{j|y=1}$ is just the fraction of the spam $(y = 1)$ emails in which word j does appear

$\phi_{j|y=0}$ is just the fraction of the spam $(y = 0)$ emails in which word j does appear

$\phi_y$ is just the fraction of the spam emails 

---

## How model works

To make a prediction on a new example with features x, we then simply calculate $p(y=1|x)$ 

$p(y=1|x)$ is given by : $$p(y=1|x) = \frac{p(x|y=1)p(y=1)}{p(x)}$$

Pick the class with highest posterior probability $p(y|x)$

---

## Extensions of Naive Bayes

Naive Bayes algorithm we looked till now is for when the features $x_j$ are binary valued

Generalization :
* If $x_j$ takes $\{1,2,,\ldots, k_j\}$ 
* Model $p(x_j|y)$ as multinomial rather than as Bernoulli

If the attributes are continuous valued, it is quite common to
discretize and apply Naive Bayes

When the original, continuous-valued attributes are not well modeled by a multivariate normal distribution, discretizing the features and using Naive Bayes (instead of GDA) will often result in a better classifier

---

## Laplace Smoothing

The Naive Bayes algorithm needs simple change that makes it work much
better (especially for text classification)

In email spam classification :
* Let us consider a word not present in the training set
* Assume that this word is $k$ th word in dictionary
* Then, let us calculate $\phi_{k|y=1} = 0$ and $\phi_{k|y=1} = 0$ 

---

## Email Spam Classification

In order to decide if one of these messages containing a unseen word is spam, It calculates the class posterior probabilities : $$p(y=1|x) = \frac{\prod_{j=1}^{d} p(x_j|y=1) p(y=1)}{\prod_{j=1}^{d} p(x_j|y=1) p(y=1) + \prod_{j=1}^{d} p(x_j|y=0) p(y=0) + } = \frac{0}{0}$$

This is because : $ \prod_{j=1}^{d} p(x_j|y)$, contains the unseen word present in the email for which the term $p(x_k|y) = 0$ gets multiplied.

---

## Laplace Smoothing

Stating the problem more broadly, it is statistically a bad idea to estimate the probability of some event to be zero just because you haven't seen
it before in your finite training set

Let us estimate the mean of multinomial random variable $z = \{z^1,z^2, \dots, z^n\}$, taking values in $\{1,2,\ldots, k\}$. The maximum likelihood estimates of the parameterized multinomial random variable is given by : $$\phi_j = \frac{\sum_{i=1}^{n} \mathbb{1\{z^i = 1\}}}{n}$$ 

---

## Laplace Smoothing

if we were to use these maximum likelihood estimates, then some of the $\phi_j$'s might end up zero

How to avoid it ?
* Laplace Smoothing
* The smoothed estimates are given by : $$\phi_j = \frac{\sum_{i=1}^{n} \mathbb{1\{z^i = 1\}}+ 1}{n + k}$$
* Note that $\sum_{i=1}^k \phi_i = 1$ still holds
* And $\phi_j \neq 0$

---

## Laplace Smoothing

With Laplace smoothing, we therefore obtain the following estimates of the parameters : $$\phi_{j|y=0} = \frac{1 +\sum_{i=1}^{n}\mathbf{1}\{x_j^i = 1\wedge y^i = 0\} }{2 + \sum_{i=1}^{n}\mathbf{1}\{y^i = 0\}}, \\ \phi_{j|y=1} = \frac{1 + \sum_{i=1}^{n}\mathbf{1}\{x_j^i = 1\wedge y^i = 1\} }{2 + \sum_{i=1}^{n}\mathbf{1}\{y^i = 1\}}$$

---

## Event Models for Text Classification

Naive Bayes we presented : 
* Works well for many classification problems
* For text classification, there is a related model that does even better

There are two models :
* Bernoulli event model or Multi-variate Bernoulli event model
* Multinomial event model

---

## Bernoulli event model

In Bernoulli event model, An email is generated :
* First randomly determine whether a spammer or non-spammer will send you your next message
* Then the person sending the email runs through the dictionary,
deciding whether to include each word $j$ in that email independently and
according to the probabilities $p(x_j=1|y) = \phi_{j|y}$
* The probability of message is given by : $p(y)\prod_{j=1}^{d} p(x_j|y)$

---

## Multinomial Event Model

Multinomial Even Model : 
* $x_j$ denote the identity of the $j$-th word in the email
* $x_j \in \{1,2,\ldots, |V|\}$, where $|V|$ is the size of the vocabulary
* Email of $d$ words is represented by $(x_1,\ldots,x_d)$

Example : 
* Let the email be "Hi, How are you ?"
* The email is represented by $[120, 51, 26, 72, 4]^T$
* Here, The word "Hi" corresponding to $120$-th letter in vocabulary and vice versa

---

## Multinomial Event Model

In the multinomial event model :
*  We assume that the way an email is generated is via a random process in which spam/non-spam is first determined
* The sender of the email writes the email by first generating words $x_i$ from some multinomial distribution over words $p(x_i|y)$ independently
* The overall probability of message is given by $p(y)\prod_{j=1}^{d} p(x_j|y)$

Though the formula looks exactly similar to that of Bernoulli event model, the $x_j|y$ is multinomial rather than a Bernoulli distribution

---

## Parameters of Multinomial Event Model

The parameters of event model are $$\phi_y = p(y), \\ \phi_{j|y=1} = p(x_j =k | y=1),\\ \phi_{j|y=0} = p(x_j =k | y=0)$$

Note that we assumed $p(x_j|y)$ same for all values of $j$ ( i.e, the distribution according to which a word is generated does not depend on its position $j$ within the email)

---

## Log Likelihood

For a given training set $\{(x^i,y^i) ; i =1,\ldots,n\}$, and training example $x^i = (x_1^i,\ldots,x_d^i)$, the likelihood of the data is given by : $$\mathcal{L}(\phi_y, \phi_{j|y=0}, \phi_{j|y=1}) = \prod_{i=1}^{n} p(x^i,y^i)\\ = \prod_{i=1}^{n} \left(\prod_{j=1}^{d_i} p(x_j^i |y;\phi_{j|y=0}, \phi_{j|y=1})\right) p(y^i;\phi_y)$$

---

## Maximum Likelihood

Maximum likelihood estimates of the parameters are given by : $$\phi_{k|y=1} \frac{\sum_{i=1}^{n} \sum_{j=1}^{d_i} \mathbb{1}\{x_j^i = k \wedge y^i =1\}}{\sum_{i=1}^{n} \mathbb{1}\{y^i =1\} d^i}, \\ \phi_{k|y=0} \frac{\sum_{i=1}^{n} \sum_{j=1}^{d_i} \mathbb{1}\{x_j^i = k \wedge y^i =0\}}{\sum_{i=1}^{n} \mathbb{1}\{y^i =0\} d^i}, \\ \phi_y = \frac{\sum_{i=1}^n \mathbb{1}\{y^i = 1\}}{n}$$

---

## Laplace Smoothing

If we were to apply Laplace smoothing : 
* For parameters $\phi_{k|y=1}$ and $\phi_{k|y=0}$, we add 1 to numerator
* Add the $|V|$ to the denominator

$$\phi_{k|y=1} =  \frac{1+ \sum_{i=1}^{n} \sum_{j=1}^{d_i} \mathbb{1}\{x_j^i = k \wedge y^i =1\}}{|V| + \sum_{i=1}^{n} \mathbb{1}\{y^i =1\} d^i}, \\ \phi_{k|y=0} \frac{1 + \sum_{i=1}^{n} \sum_{j=1}^{d_i} \mathbb{1}\{x_j^i = k \wedge y^i =0\}}{|V| + \sum_{i=1}^{n} \mathbb{1}\{y^i =0\} d^i}$$

---

## Conclusions

Naive Bayes Algorithm :
* Not necessarily the very best classification algorithm
* Often works surprisingly well. 
* It is often also a very good "first thing to try" given its simplicity and ease of implementation.

---