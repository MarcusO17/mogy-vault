---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - regularization
---

# Dropout

**Dropout** is a powerful regularization technique used in deep neural networks to prevent overfitting. It works by randomly "dropping out" (setting to zero) a fraction of neurons during each training step.

---

## Mechanism & Implementation

### 1. Training Phase
At each training step, for a given layer, we define a dropout probability $p$ (the probability of dropping a neuron). We construct a binary mask vector $\mathbf{v}$ of the same dimension as the activation vector $\mathbf{a}$:

$$
v_i \sim \text{Bernoulli}(1 - p) \implies v_i = \begin{cases} 0 & \text{with probability } p \\ 1 & \text{with probability } 1 - p \end{cases}
$$

The activations are then zeroed out using the element-wise (Hadamard) product:
$$
\mathbf{a}_{\text{dropped}} = \mathbf{a} \odot \mathbf{v}
$$

### 2. Inference Phase & Scaling
During inference, dropout is turned off ($p = 0$) to utilize the full network's capacity. Since all neurons are active, the expected magnitude of the activations will be higher than during training. 

To resolve this scale mismatch, there are two approaches:
* **Standard Dropout**: During training, activations are unmodified. During inference, the activations must be scaled down to match the training scale:
  $$
  \mathbf{a}_{\text{inference}} = \mathbf{a} \cdot (1 - p)
  $$
* **Inverted Dropout (Modern standard used in PyTorch)**: To avoid scaling at inference time, the activations are scaled *up* during the training phase instead:
  $$
  \mathbf{a}_{\text{training}} = \frac{\mathbf{a} \odot \mathbf{v}}{1 - p}
  $$
  This ensures that the expected value of the activations remains constant, allowing the inference pass to run without any modifications.

---

## Why Dropout Works
1. **Prevents Co-adaptation**: A neuron cannot rely on the presence of other specific neurons to extract features. It is forced to learn robust features that are useful in combination with random subsets of other neurons.
2. **Ensemble Approximation**: Dropout can be viewed as training an ensemble of $2^N$ sub-networks (where $N$ is the number of neurons) with shared weights. At test time, using the full scaled network acts as an approximation of averaging the predictions of all these sub-networks.
3. **Weight Shrinkage**: By forcing the network to distribute representation across many units, it spreads out weight values, exhibiting a regularization effect similar to [[L1 L2 Regularization|L2 regularization]].

---
*From* → [[Regularization]]
