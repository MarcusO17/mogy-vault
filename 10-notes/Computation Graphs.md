---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/backprop
---

# Computation Graphs

A **Computation Graph** is a directed graph that represents a mathematical expression or function. In deep learning frameworks like PyTorch, neural networks are represented as computation graphs where:
- **Nodes** represent operations (e.g., addition, multiplication, activation functions).
- **Edges** represent tensors (data) flowing between these operations.

Computation graphs consist of two main phases:
1. **Forward Pass**: Constructs the graph and computes the output values.
2. **Backward Pass**: Computes the gradients of the output (loss) with respect to all parameters using the chain rule (backpropagation).

---

### Tracing a Computation Graph with ReLU
Consider a simple linear layer with a [[ReLU Function|ReLU]] activation:
- $u = w \cdot x$
- $v = u + b$
- $a = \text{ReLU}(v)$

For machine learning purposes, the derivative of the ReLU function $\text{ReLU}(z) = \max(0, z)$ is defined as:
$$
\text{ReLU}'(z) = \begin{cases} 
0 & \text{if } z \le 0 \\ 
1 & \text{if } z > 0 
\end{cases}
$$

#### Tracing the Forward Pass
Let $x = 3$, $w = 2$, and $b = 1$:
- $u = 2 \cdot 3 = 6$
- $v = 6 + 1 = 7$
- $a = \text{ReLU}(7) = 7$

#### Tracing the Backward Pass (Chain Rule)
To update the parameters $b$ and $w$, we compute their partial derivatives with respect to the output $a$:

1. **Gradient with respect to bias ($b$)**:
   $$
   \frac{\partial a}{\partial b} = \frac{\partial v}{\partial b} \cdot \frac{\partial a}{\partial v} = 1 \cdot \text{ReLU}'(v) = 1 \cdot 1 = 1
   $$

2. **Gradient with respect to weight ($w$)**:
   $$
   \frac{\partial a}{\partial w} = \frac{\partial u}{\partial w} \cdot \frac{\partial v}{\partial u} \cdot \frac{\partial a}{\partial v} = x \cdot 1 \cdot \text{ReLU}'(v) = 3 \cdot 1 \cdot 1 = 3
   $$

---
*From* → [[the PyTorch Process]]
