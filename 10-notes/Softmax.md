---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Softmax

The **Softmax function** (or Softmax activation) is a generalization of the logistic [[Sigmoid Function]] to multi-class classification tasks. It maps a vector of raw prediction scores ([[Logits]]) to a probability distribution over the target classes.

**basically it's a exponential function which normalizes the activations so that they all sum up to 1**.

---

## Multiclass Classification Motivation
While binary classification tasks use a single sigmoid node to predict a probability $P(y=1 \mid \mathbf{x})$, multi-class tasks require predicting a probability for each of $K$ different classes. 

Instead of training multiple independent binary classifiers (the [[One-vs-Rest Classification|One-vs-Rest]] approach), a single model can output $K$ logits, which are normalized using the Softmax function into a joint probability distribution where the probabilities are non-negative and sum to exactly $1.0$.

---

## Mathematical Formulation
For a training instance $i$, given a vector of $K$ logits $\mathbf{z}^{[i]} = [z_1^{[i]}, \dots, z_K^{[i]}]^\top$, the Softmax probability for class $c \in \{1, \dots, K\}$ is:

$$
a_c^{[i]} = \sigma_{\text{softmax}}(\mathbf{z}^{[i]})_c = \frac{e^{z_c^{[i]}}}{\sum_{j=1}^{K} e^{z_j^{[i]}}}
$$

### Interpretation of Terms
1. **Numerator ($e^{z_c^{[i]}}$)**: The exponential function maps the real-valued logits to strictly positive values, ensuring that no class probability is negative.
2. **Denominator ($\sum_{j=1}^{K} e^{z_j^{[i]}}$)**: Normalizes the positive values by dividing each by the sum of all exponentials. This ensures that the output vector elements sum to $1.0$:
   $$
   \sum_{c=1}^{K} a_c^{[i]} = 1.0
   $$

---

## Making Predictions (Argmax)
To generate a final class prediction $\hat{y}$ from the Softmax probability vector, the **argmax** operation is applied, selecting the index of the class with the highest probability:

$$
\hat{y}^{[i]} = \arg\max_{c} a_c^{[i]}
$$

---
*From* → [[Non-Linear Activation Functions]]
