---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# Dead Neurons

The **Dying ReLU** or **Dead Neurons** problem is a phenomenon where certain neurons in a deep neural network using the [[ReLU Function]] permanently stop updating and always output zero, effectively becoming inactive.

---

## Mechanism of Neuron Death
A neuron $n$ dies when its net input (the weighted sum of inputs plus bias) is negative for all examples in the training dataset:

1. **Zero Output**: Because $\text{ReLU}(z) = \max(0, z)$, the output is $0$ whenever the input $z \le 0$.
2. **Zero Gradient**: The derivative of ReLU is zero for negative inputs ($\text{ReLU}'(z) = 0$ for $z \le 0$). This contributes to the [[Vanishing Gradients]] problem for the layers behind it.
3. **No Weight Updates**: Since the gradient is zero, backpropagation cannot flow through this neuron, and the weights feeding into it are never updated. The neuron is trapped in a state where it always outputs zero and cannot recover.

> [!NOTE] Regularization Effect
> A small percentage of dead neurons is not necessarily harmful; it introduces sparsity in the network representations, which can act as a form of implicit regularization.

---

## Causes of Dead Neurons

1. **Poor Weight Initialization**: If weights or biases are initialized to be too negative, neurons can start the training process already dead. This is mitigated using proper techniques like [[Kaiming He Initialization]].
2. **High Learning Rate**: A large learning rate can cause parameter updates to "overshoot." An active neuron's weights might be updated so drastically that its net input is pushed deep into the negative zone, causing it to die.
3. **Negative Weights or Large Negative Bias**: Strongly negative parameters can force the net input to remain below zero regardless of the previous layer's activations.

---
*From* → [[ReLU Function]]
