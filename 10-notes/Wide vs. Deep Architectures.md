---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - backpropagation
---

# Wide vs. Deep Architectures

A fundamental design choice in neural network architecture is whether to make a network **wide** (many units in a few layers) or **deep** (fewer units in many stacked layers).

---

## The Universal Approximation Theorem
The **Universal Approximation Theorem** states that a feed-forward network with a single hidden layer and a non-linear activation function can approximate any continuous function on a compact subset of $\mathbb{R}^n$ to any desired degree of accuracy.

If a single hidden layer is theoretically sufficient to learn any function, why do we use deep networks?

---

## Why Deep is Better Than Wide

### 1. Parameter Efficiency (Exponential Savings)
While a shallow, single-layer network can theoretically approximate any function, doing so may require an exponentially large number of hidden units (parameters). Stacking layers hierarchically allows the network to represent complex functions with exponentially fewer parameters.

### 2. Hierarchical Feature Learning
Deep networks learn features in a hierarchical, compositional manner:
* **Lower layers**: Capture simple local features (e.g., edges, lines in images).
* **Middle layers**: Combine lower-level features to detect textures and motifs.
* **Higher layers**: Combine middle features to represent semantic concepts (e.g., objects, faces).

Shallow networks cannot build this hierarchy, forcing them to learn complex, global mappings in a single step, which is far less efficient.

---

## Practical Challenges of Deep MLPs
Historically, training networks deeper than $2$ or $3$ layers was highly unstable due to:
* **[[Vanishing Gradients]] / [[Exploding Gradients]]**: As gradients propagate backward through many layers, they either shrink exponentially to zero or grow exponentially, preventing early layers from updating stably.
* These issues were later solved using modern techniques such as [[Weight Initialization|He/Xavier initialization]], [[Normalization|Batch Normalization]], residual connections, and advanced optimizers like [[ADAM]].

---
*From* → [[MLP]]
