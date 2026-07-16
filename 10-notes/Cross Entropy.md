---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Cross Entropy

**Cross Entropy** is a loss function widely used in classification tasks. It measures the difference between the predicted probability distribution output by a model and the true probability distribution of the target labels.

---

## 1. Binary Cross-Entropy (BCE)
Used for binary classification tasks (where targets $y^{[i]} \in \{0, 1\}$). For a single training instance $i$, the BCE loss is defined as:

$$
\mathcal{L}_i = - \left[ y^{[i]} \log(\hat{y}^{[i]}) + (1 - y^{[i]}) \log(1 - \hat{y}^{[i]}) \right]
$$

where $\hat{y}^{[i]} = \sigma(z^{[i]})$ is the predicted probability of the positive class (using the [[Sigmoid Function]]).
- If $y^{[i]} = 1$, the loss is $- \log(\hat{y}^{[i]})$. To minimize this, we want $\hat{y}^{[i]} \to 1$.
- If $y^{[i]} = 0$, the loss is $- \log(1 - \hat{y}^{[i]})$. To minimize this, we want $\hat{y}^{[i]} \to 0$.

BCE is equivalent to minimizing the negative log-likelihood of a Bernoulli distribution, commonly used in [[Logistic Regression]].

---

## 2. Categorical Cross-Entropy (CCE)
Used for multi-class classification tasks (where targets are [[10-notes/One-Hot Encoding|one-hot encoded]] vectors of size $K$). Across $n$ training instances, the CCE loss is:

$$
\mathcal{L} = -\sum_{i=1}^{n} \sum_{j=1}^{K} y_j^{[i]} \log(a_j^{[i]})
$$

where $y_j^{[i]}$ is the true label (1 if class $j$ is correct, 0 otherwise), and $a_j^{[i]}$ is the model's predicted probability for class $j$ (typically output by the [[Softmax]] function).
Because of one-hot encoding, the inner sum collapses to check only the predicted probability of the correct target class.

---

## Why Use the Logarithm?

1. **Asymmetric Penalties**: The logarithm function $-\log(p)$ severely penalizes incorrect predictions. Being confidently wrong (e.g., predicting $0.01$ when the true class is $1$) results in a massive penalty ($-\log(0.01) \approx 4.6$), whereas predicting $0.99$ yields a negligible penalty ($-\log(0.99) \approx 0.01$).
2. **Numerical Stability**: Multiplying many small probabilities together can cause **numerical underflow** (rounding to absolute zero). The logarithm transforms multiplications into additions: $\log(a \cdot b) = \log(a) + \log(b)$, which is numerically stable.
3. **Connection to MLE**: Minimizing cross-entropy is mathematically equivalent to maximizing the likelihood of the training data under the model's parameters (see [[Maximum Log-Likelihood]]).

---
*From* → [[Loss Functions]]
