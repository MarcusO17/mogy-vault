---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Notational Conventions in Deep Learning

Consistency in mathematical notation is essential for implementing and debugging deep learning algorithms. Below are the standard conventions used for vectors, matrices, and forward pass computations.

---

## 1. Single Example Representation (Vectorized)
For a single training example, feature and weight vectors are typically represented as **column vectors**:
- $\mathbf{x} \in \mathbb{R}^{m \times 1}$ (where $m$ is the number of features).
- $\mathbf{w} \in \mathbb{R}^{m \times 1}$ (weights).
- $b \in \mathbb{R}$ (bias scalar).

To compute the net input $z$, the feature vector is transposed ($^\top$) to perform a dot product:
$$
z = \mathbf{w}^\top \mathbf{x} + b
$$

---

## 2. Multi-Neuron / Layer Representation (Matrix-Vector)
When a layer has $h$ hidden units (outputs) and receives $m$ inputs:
- The weights are represented as a weight matrix $\mathbf{W} \in \mathbb{R}^{h \times m}$.
- The bias is represented as a vector $\mathbf{b} \in \mathbb{R}^{h \times 1}$.

The forward pass (inference) for a single example $\mathbf{x}$ yielding activations $\mathbf{a}$ is:
$$
\mathbf{a} = \sigma(\mathbf{W}\mathbf{x} + \mathbf{b}) \quad \text{where } \mathbf{a} \in \mathbb{R}^{h \times 1}
$$

---

## 3. Dataset Representation (Design Matrix)
To process $n$ training examples simultaneously, we stack the feature vectors horizontally or vertically into a **design matrix** $\mathbf{X}$:
- $\mathbf{X} \in \mathbb{R}^{n \times m}$ (where each row represents a single training example).
- $\mathbf{w} \in \mathbb{R}^{m \times 1}$ (for a single output unit).
- $\mathbf{z} \in \mathbb{R}^{n \times 1}$ (net inputs for all examples).

The vectorized forward pass across all $n$ examples is:
$$
\mathbf{z} = \mathbf{X}\mathbf{w} + b
$$
*(where the scalar bias $b$ is broadcasted to add to each element of the resulting vector).*

---
*From* → [[Common Math Notation]]
