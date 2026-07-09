---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Weight Initialization

**Weight Initialization** is the process of setting the initial weights and biases of a neural network's layers before training begins. Proper initialization is critical for training deep neural networks successfully.

---

## Why Proper Initialization Matters

### 1. Symmetry Breaking
If all weights in a layer are initialized to the same constant value (such as all zeros or all ones), every neuron in that layer will compute the exact same activation during the forward pass. Consequently, they will receive the exact same gradient during backpropagation and perform identical updates. This prevents the network from learning diverse features, rendering hidden units redundant. Random initialization breaks this symmetry.

### 2. Preventing Exploding & Vanishing Activations/Gradients
* **Weights Too Large (Exploding)**: Activations grow exponentially as they propagate deeper. This forces inputs to activation functions (like [[Sigmoid Function|Sigmoid]] or Tanh) into their saturated plateau regions. Since the derivatives in these regions are near zero, the gradients vanish (the [[Vanishing Gradients]] problem), halting learning.
* **Weights Too Small (Vanishing)**: Activations shrink exponentially, quickly collapsing to zero. The gradients also shrink exponentially across layers, preventing early layers from updating.

---

## Initialization Strategies

### 1. Traditional Random Initialization
Weights are sampled from a small random uniform or normal distribution (e.g., $W \sim \mathcal{U}(-0.01, 0.01)$). While this breaks symmetry, it fails for deeper networks as the variance of activations still scales with the number of input nodes.

### 2. Xavier (Glorot) Initialization
Designed for layers using symmetric activations like tanh or sigmoid. It scales variance based on input and output dimensions:
* *See more* → [[Xiaver Glorot Initialization]]

### 3. Kaiming (He) Initialization
Designed specifically for rectified activation functions like [[ReLU Function|ReLU]]. It compensates for the deactivation of half of the nodes by doubling the initial variance:
* *See more* → [[Kaiming He Initialization]]

---
*From* → [[Improving Generalization]]
