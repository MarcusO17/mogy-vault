---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/training/normalization
  - dl/architecture/cnn
---

# Local Response Normalisation

**Local Response Normalisation** (LRN) is a normalization layer first introduced in [[AlexNet]] to aid generalization. It implements a form of **lateral inhibition** inspired by biological neurons, creating competition for large activations among neuron outputs computed using different kernels (channels) at the same spatial position.

---

## Mathematical Formulation
For a neuron activation $a_c$ computed by kernel $c$ at a specific spatial position, its normalized activation $b_c$ is defined as:

$$
b_{c} = a_{c}\left(k + \frac{\alpha}{n} \sum_{c'=\max(0, c-n/2)}^{\min(N-1,c+n/2)}a_{c'}^2\right)^{-\beta}
$$

where:
- $N$ is the total number of channels (kernels).
- $n$ is the number of adjacent channels over which the normalization is computed.
- $a_{c'}$ is the activation of the neuron in adjacent channel $c'$ at the same spatial position.
- $k$, $\alpha$, and $\beta$ are hyperparameters. In the AlexNet paper, these were set to $k = 2$, $n = 5$, $\alpha = 10^{-4}$, and $\beta = 0.75$.

---

## Conceptual Mechanism
* **Cross-Channel Competition**: LRN normalizes a neuron's activation by dividing it by the activity of its neighboring channels. If neighboring channels have very large activations, the current neuron's activation will be scaled down.
* **Modern Status**: LRN is rarely used in modern architectures, having been largely superseded by [[Normalization|Batch Normalization]] which is generally more effective and computationally simpler.

---
*From* → [[AlexNet]]
