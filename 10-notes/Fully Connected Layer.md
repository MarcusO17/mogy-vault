---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/architecture/mlp
---

# Fully Connected Layer

A **Fully Connected Layer** (also known as a **Linear Layer** in PyTorch or **Dense Layer** in TensorFlow) is a standard neural network layer where every input neuron is connected to every output neuron.

---

## Mathematical Formulation
For an input vector $\mathbf{x} \in \mathbb{R}^{d_{\text{in}}}$, the output of a fully connected layer $\mathbf{y} \in \mathbb{R}^{d_{\text{out}}}$ is computed via a matrix-vector multiplication followed by a bias addition:

$$
\mathbf{y} = \mathbf{W}\mathbf{x} + \mathbf{b}
$$

where:
- $\mathbf{W} \in \mathbb{R}^{d_{\text{out}} \times d_{\text{in}}}$ is the weight matrix.
- $\mathbf{b} \in \mathbb{R}^{d_{\text{out}}}$ is the bias vector.

![[Pasted Image 20250814182920_027.png]]

---

## PyTorch Implementation
In PyTorch, a fully connected layer is created using the `torch.nn.Linear` module:

```python
import torch.nn as nn

# Input dimension: 10, Output dimension: 5
linear_layer = nn.Linear(in_features=10, out_features=5)
```

---
*From* → [[MLP]]
