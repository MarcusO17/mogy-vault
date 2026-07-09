---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# The Perceptron

The **Perceptron** is one of the earliest models of an artificial neuron, introduced by Frank Rosenblatt in 1957. It forms the foundation of modern neural networks, acting as a linear binary classifier.

---

## Evolution of the Model

### 1. McCulloch & Pitts Neuron (1943)
A simple binary model where input features are summed and compared to a threshold:
$$
\sum_{i=1}^{m} x_i w_i = Z
$$

### 2. Rosenblatt's Perceptron (1957)
Rosenblatt added learnable weights and a threshold activation function $f_\theta$:
$$
\hat{y} = f_\theta\left(\sum_{i=1}^{m} x_i w_i\right)
$$

### 3. Single-Layer Neural Network Formulation
Modern notation represents the threshold $\theta$ as a learnable bias term $b = -\theta$, mapping inputs to a step activation function $\sigma(z)$:

$$
\hat{y} = \sigma(\mathbf{w}^\top \mathbf{x} + b)
$$
$$
\sigma(z) = \begin{cases} 
0 & \text{if } z \le 0 \\ 
1 & \text{if } z > 0 
\end{cases}
$$

![[Pasted image 20250810171854.png]]

---

## Perceptron Learning Algorithm

Given a training dataset $\mathcal{D} = \{\langle \mathbf{x}^{[1]}, y^{[1]} \rangle, \dots, \langle \mathbf{x}^{[n]}, y^{[n]} \rangle\}$ where $\mathbf{x} \in \mathbb{R}^m$ and $y \in \{0, 1\}$:

1. Initialize weights $\mathbf{w} := \mathbf{0} \in \mathbb{R}^m$ and bias $b := 0$.
2. For each training epoch:
   1. For each training example $\langle \mathbf{x}^{[i]}, y^{[i]} \rangle \in \mathcal{D}$:
      1. Compute the prediction: $\hat{y}^{[i]} := \sigma(\mathbf{w}^\top \mathbf{x}^{[i]} + b)$
      2. Calculate the error: $\text{err} := y^{[i]} - \hat{y}^{[i]}$
      3. Update weights and bias:
         $$
         \mathbf{w} := \mathbf{w} + \text{err} \cdot \mathbf{x}^{[i]}
         $$
         $$
         b := b + \text{err}
         $$

### Convergence
The Perceptron learning algorithm is guaranteed to converge to a separating hyperplane if and only if the dataset is **linearly separable** (the Perceptron Convergence Theorem). If the data is not linearly separable, the algorithm will oscillate indefinitely.

---
*From* → [[Supervised Learning]]
