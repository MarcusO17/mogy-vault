---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - activation-functions
---

# ReLU Function

The **Rectified Linear Unit (ReLU)** is the most widely used activation function in deep learning. It outputs the input directly if it is positive; otherwise, it outputs zero.

---

## Mathematical Formulation
The ReLU function is defined as:

$$
f(z) = \max(0, z)
$$

### Derivative
The mathematical derivative of ReLU is not defined at exactly $z = 0$. However, in machine learning implementations, we use a subgradient that is defined at $0$:

$$
f'(z) = \begin{cases} 
0 & \text{if } z \le 0 \\ 
1 & \text{if } z > 0 
\end{cases}
$$

---

## Advantages
* **Computational Efficiency**: Extremely fast to compute compared to sigmoid or tanh, as it only requires a thresholding operation ($z > 0$) rather than exponential calculations.
* **Reduces Vanishing Gradients**: For positive inputs ($z > 0$), the gradient is a constant $1$. This allows gradients to flow through deep networks without being exponentially scaled down.
* **Sparsity**: Since it outputs exactly $0$ for negative inputs, it naturally creates sparse activations where only a subset of neurons are active simultaneously.

---

## Limitations
* **Dying ReLU / Dead Neurons**: If a neuron receives negative inputs for all examples in the dataset, its gradient is always zero. The weights will stop updating, and the neuron will permanently "die" (always outputting zero).
  * *See more* → [[Dead Neurons]]

---
*From* → [[Non-Linear Activation Functions]]
