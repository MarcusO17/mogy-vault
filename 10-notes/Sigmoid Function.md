---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/activation
---

# Sigmoid Function

The **logistic sigmoid function** is a non-linear activation function that maps any real-valued number to a value between $0$ and $1$. It is commonly used in binary classification models to output probabilities.

---

## Mathematical Formulation
The sigmoid function is defined as:

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

### Derivative
The derivative of the sigmoid function has a convenient form that can be computed directly from its output:

$$
\sigma'(z) = \sigma(z)(1 - \sigma(z))
$$

---

## Characteristics & Limitations
* **Probability Mapping**: Since the output range is $(0, 1)$, it is ideal for models that predict probabilities (e.g., [[Logistic Regression]]).
* **Not Zero-Centered**: The output of the sigmoid function is always positive. This can cause the gradients during backpropagation to all have the same sign (either all positive or all negative), which can introduce zig-zagging dynamics during gradient descent optimization.
* **Saturation & Vanishing Gradients**: For very high or very low values of $z$, the curve plateaus, and the derivative $\sigma'(z)$ approaches $0$. In deep networks, this causes gradients to become extremely small (the [[Dead Neurons|vanishing gradient]] problem), halting the updates to the weights.

---
*From* → [[Non-Linear Activation Functions]]
