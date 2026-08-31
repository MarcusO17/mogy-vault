---
created: 2026-07-09
type: note
status: draft
topic: [statistics, ML]
tags:
  - dl/training/loss
---

# Maximum Log-Likelihood

**Maximum Likelihood Estimation (MLE)** is a method in statistics used to estimate the parameters of a probability distribution by maximizing a **likelihood function**, so that the observed data is most probable under the assumed statistical model.

---

## The Likelihood Function
Given a dataset of independent and identically distributed (i.i.d.) observations $\mathbf{X} = \{x^{[1]}, \dots, x^{[n]}\}$ and a model parameterized by $\theta$, the joint probability (likelihood) of observing this data is:

$$
\mathcal{L}(\theta \mid \mathbf{X}) = \prod_{i=1}^{n} P(x^{[i]} \mid \theta)
$$

### Taking the Logarithm (Log-Likelihood)
Maximizing the product directly can lead to **numerical underflow** on computer systems, as multiplying many small probabilities together quickly results in values that round to absolute zero. 

To resolve this, we take the natural logarithm of the likelihood function. Because the logarithm is a monotonically increasing function, the value of $\theta$ that maximizes the log-likelihood also maximizes the original likelihood:

$$
\log \mathcal{L}(\theta \mid \mathbf{X}) = \sum_{i=1}^{n} \log P(x^{[i]} \mid \theta)
$$

Taking the log transforms the product into a sum, which is numerically stable and simplifies computing derivatives during optimization.

---

## Connection to Loss Functions
In machine learning, we typically minimize a loss function rather than maximizing a likelihood. We achieve this by negating the log-likelihood:

$$
J(\theta) = - \log \mathcal{L}(\theta \mid \mathbf{X})
$$

Minimizing this **Negative Log-Likelihood (NLL)** is mathematically equivalent to maximizing the likelihood of the data. For example:
* For a Bernoulli distribution (binary classification), NLL is identical to [[Cross Entropy#Binary Cross-Entropy|Binary Cross-Entropy]].
* For a Gaussian distribution (regression), maximizing log-likelihood is equivalent to minimizing [[Loss Functions#1. Regression Loss Functions|Mean Squared Error]].

---
*From* → [[Logistic Regression]]
