---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/architecture/rnn
---

# Recurrent Neural Networks

**Recurrent Neural Networks** (RNNs) are a class of neural network architectures designed specifically for [[Sequence Modelling]] tasks. Unlike feed-forward networks (like MLPs), RNNs maintain a internal hidden state that acts as memory, allowing information to persist across sequential steps.

---

## Model Architecture & Forward Pass

At each time step $t$, the hidden state $\mathbf{h}^{\langle t \rangle}$ is updated using the current input vector $\mathbf{x}^{\langle t \rangle}$ and the previous hidden state $\mathbf{h}^{\langle t-1 \rangle}$:

### 1. Hidden State Update
- **Net Input**:
  $$
  \mathbf{z}_{h}^{\langle t \rangle} = \mathbf{W}_{hx}\mathbf{x}^{\langle t \rangle} + \mathbf{W}_{hh}\mathbf{h}^{\langle t-1 \rangle} + \mathbf{b}_{h}
  $$
- **Activation**:
  $$
  \mathbf{h}^{\langle t \rangle} = \tanh(\mathbf{z}_{h}^{\langle t \rangle})
  $$
  *(where $\mathbf{W}_{hx}$ maps input to hidden state, and $\mathbf{W}_{hh}$ maps hidden state to hidden state).*

### 2. Output Calculation
The network computes outputs $\hat{\mathbf{y}}^{\langle t \rangle}$ from the current hidden state:
- **Net Input**:
  $$
  \mathbf{z}_y^{\langle t \rangle} = \mathbf{W}_{yh}\mathbf{h}^{\langle t \rangle} + \mathbf{b}_y
  $$
- **Output Activation**:
  $$
  \hat{\mathbf{y}}^{\langle t \rangle} = \text{Softmax}(\mathbf{z}_y^{\langle t \rangle}) \quad (\text{or other output activations})
  $$

![[Pasted image 20251128205445.png]]

---

## Backpropagation Through Time (BPTT)
RNNs are trained using **Backpropagation Through Time (BPTT)**. The forward pass unfolds the graph across all time steps, and the backward pass computes gradients by accumulating derivatives backwards through the sequence.

Because gradients are multiplied repeatedly across many time steps during BPTT, RNNs suffer heavily from the **vanishing and exploding gradient** problems. This makes it difficult for standard RNNs to capture long-range dependencies, leading to the development of architectures like [[Long Short-Term Memory|LSTMs]].

![[Pasted image 20251206155015.png]]

---
*From* → [[Sequence Modelling]]
