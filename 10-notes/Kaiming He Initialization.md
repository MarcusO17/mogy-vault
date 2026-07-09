---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Kaiming He Initialization

**Kaiming He Initialization** (also known as **He Initialization**) is a weight initialization method designed for deep neural networks that use rectified activation functions such as [[ReLU Function|ReLU]] or Leaky ReLU. 

It is designed to ensure that the variance of activations and gradients remains stable across layers, preventing the signal from vanishing or exploding as it propagates through deep networks.

---

## Mathematical Formulation

For a layer with $m_{\text{in}}$ input connections (fan-in):

### 1. Normal Distribution
Weights are sampled from a zero-mean Gaussian distribution with a variance of $\frac{2}{m_{\text{in}}}$:
$$
W \sim \mathcal{N}\left(0, \frac{2}{m_{\text{in}}}\right)
$$

### 2. Uniform Distribution
Alternatively, weights can be sampled from a uniform distribution:
$$
W \sim \mathcal{U}\left(-\sqrt{\frac{6}{m_{\text{in}}}}, \sqrt{\frac{6}{m_{\text{in}}}}\right)
$$

---

## Intuition & Comparison with Xavier
Because the [[ReLU Function|ReLU]] activation function sets all negative values to zero, on average **half of the neurons in a layer are deactivated** at any given time step. This halves the variance of the activations flowing to the next layer. If this reduction accumulates over many layers, the signal will exponentially shrink (vanish).

* **Xavier Glorot Initialization** (designed for symmetric activations like tanh) assumes all neurons are active and sets the variance to $\frac{1}{m_{\text{in}}}$ (or $\frac{2}{m_{\text{in}} + m_{\text{out}}}$).
* **He Initialization** compensates for the ReLU deactivations by **doubling the variance** to $\frac{2}{m_{\text{in}}}$. In short: *ReLU halves the signal variance; He initialization doubles the starting variance to balance it.*

---
*From* → [[Weight Initialization]]
