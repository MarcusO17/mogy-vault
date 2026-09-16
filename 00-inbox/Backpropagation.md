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

So if we think about a Neural Network with 1 million nodes, there will be nearly 2 millions things to update, 1 million weights and 1 million biases. And since we can't just nudge it all at once, ( as mentioned in [[micrograd]], we will not know where to go). We will perform partial derivation on each node, so to just understand how should we fix this particular node? That will take 2 million computations to know what to do next. Not even the final solution but what to do next. So we can imagine, how long will it take for us to achieve minimum loss?

This is the beauty of Backpropagation. 

We are able to get all $\frac{ \partial \mathcal{L} }{ \partial w_{j} }$ in 1 single backward pass, as compared to 2 million passes. But how?
Let's take a $w$, at layer $l$, on node $j$ going to node $k$ , $$w^{l}_{jk}$$

Let's say that we just got ran a forward pass, and calculated the loss of the whole network $\mathcal{L}$ , We now wanna find out, how much did $w^{l}_{jk}$  change the networks loss, $\mathcal{L}$? (Like the cake's analogy in [[micrograd]]) So remember we don't have to know if it was good or bad, that's up to the learning algorithms, we merely have to know, the sensitivity (like if we change this weight again, how much is the loss affected) and also remember how much of the weight did we nudge to produce that change in the loss.

This can be represented by 

$$
\begin{align}
\text{Change in loss}  &= \text{Sensitivity of weight} \cdot \text{Actual weight change}
\end{align}
	 
$$
I mean it's rather common sense that, the loss changed by the weight change and how important/sensitive that weight was to the loss. 

So that can be explained in mathematical terms:
$$
	\Delta \mathcal{L} = \frac{ \partial \mathcal{L} }{ \partial w^{l}_{jk} }\cdot \Delta w^{l}_{jk}
$$
So we have to trace what has $w^{l}_{jk}$ touched before this till the output as they would have affected each other, like tugging a chain of buoys, (OO Chain Rule).  We can get how much did the neural network loss change by changing that weight. So that weight change, also affected the inputs of many other nodes along the way, which affected many more nodes along the way, 

So for this case let's assume that the path of the nodes are $k \to p \to \dots \to m\to n$
And the aforementioned inputs are the previous nodes activations (in simpler terms, incoming output from the previous nodes) which is denoted as $a$ (similar to net input). The formula for net input:
$$
	a =\sigma( wx+b)
$$
where $wx+b$ is the net input denoted as z and $\sigma$ is the activation function.

To see how much the activations changed,
$$
	\frac{ \partial a }{ \partial w } = \frac{ \partial  }{ \partial \sigma } \cdot \frac{ \partial \sigma }{ \partial x } 
$$




















---
