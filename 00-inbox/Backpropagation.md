---
created: 2026-09-16
type: note
status: draft
---
---

# Backpropagation


As we are aware, the training of neural networks are to figure out a truth value, and discover how far are we from this truth value, and how should we then change our approach to handling the input data to get closer to the truth value. This is called [[gradient Descent]], where we nudge parameters of the neural network, to reduce loss (how far are we to the ideal answer). How much should we nudge it, is the gradient of the loss graph, and if we can reduce the gradient $\to 0$ then we have achieved the best possible answer. 

In order to compute this gradient, we utilize **Backpropagation**,

This algorithm has only 1 job, which is based on the current parameters (weights and bias values) how much does the **current**  node affect how far the answer is from the truth value (loss).
$$
\frac{ \partial \mathcal{L} }{ \partial w }, \quad \frac{ \partial \mathcal{L} }{ \partial b }  
$$
>[!note]
>If I were to nudge/adjust $w$ or  $b$, how much would $\mathcal{L}$ change?

Backpropagation does not actually make the network learn but only provides the gradients to let algorithms like [[ADAM]] or [[Stochastic Gradient Descent]] to learn from.

## Beauty of Backprop

So if we think about a Neural Network with 1 million nodes, there will be nearly 2 millions things to update, 1 million weights and 1 million biases. And since we can't just nudge it all at once, ( as mentioned in [[micrograd]], we will not know where to go). We will perform partial derivation on each node, to just understand how should we fix this particular node? That will take 2 million computations to know what to do next. Not even the final solution but what to do next. So we can imagine, how long will it take for us to achieve minimum loss?





















---
