---
created: 2026-06-18
type: note
status: draft
topic: ML
tags:
  - weight-init
  - activation-functions
---

# Xiaver Glorot Initialization

When using TanH, it is more robust against vanishing gradients however it's still faces the problem. We can use Xiaver Glorot Initialisation for initialising weights of TanH.

![[Pasted image 20251021082513.png]]

---
## Process
1. Initialise weights from gaussian or Uniform Distribution.
2. Scale the weights proportional to the number of inputs to the layer
   $$
\mathbf{W}^{(l)} = \mathbf{W}^{(l)} \cdot \sqrt{ \frac{1}{m^{(l-1)}} } 
$$


![[Pasted image 20251021095113.png]]

---
Xavier initialization works well for tanh activations but poorly for ReLU because the assumptions underlying each activation function differ. The goal of any weight initialization scheme is to keep the variance of activations and gradients roughly constant across layers, preventing exploding or vanishing signals during forward and backward propagation.

Xavier (or Glorot) initialization assumes that the activation function is approximately linear and symmetric around zero. It sets the weight variance to $( Var(W) = \frac{2}{n_{in} + n_{out}} )$,  which balances the flow of information both forward and backward through the network. This works well for activations like tanh or sigmoid, which are centered at zero and produce outputs that can be both positive and negative. Because tanh activations preserve a roughly zero mean and symmetrical distribution, the Xavier assumption holds, maintaining stable variance through layers.

ReLU activations, however, violate these assumptions. A ReLU zeroes out all negative inputs, meaning that only about half of the neurons are active at any given time. As a result, the output distribution is no longer centered at zero, and its variance is roughly half that of the input. When Xavier initialization is used with ReLU, it underestimates the necessary variance, causing activations and gradients to shrink as they propagate through the network. This leads to vanishing activations and slower or failed training.

To correct for this, [[Kaiming He Initialization|| Kaiming He]] initialization was introduced.


*From* →
