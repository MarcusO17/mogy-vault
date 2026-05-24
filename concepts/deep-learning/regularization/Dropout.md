Created : 2025-10-13 21:34
Tags :
Type :
Lecture : #L10
Video : https://www.youtube.com/watch?v=Va4K-wYh_p8

---
# Dropout
Basically, It's about dropping nodes randomly during training. Depending on the dropout probability. The node won't be used/deleted during the forward pass. For ex, if the dropout probability is 0.5, there's a 50% chance a node won't be used during that forward pass.

![[Pasted image 20251013213429.png]]

---
## How is Dropout implemented?

So how can Dropout be carried out efficiently without altering much of the architecture implementation.

Use Bernoulli Sampling while training :

* *p* := drop probability
* **v** := random sample from uniform distribution in range $[0,1]$
* $\forall i \in \mathbf{v} : v_{i} := \begin{cases} 0 & \text{if } v_i < p \\ 1 & \text{if } v_i \ge p \end{cases}$
* $\mathbf{a} := \mathbf{a} \odot \mathbf{v}$

So, the dropout sampling technique is defined using a hyperparameter ***p***, which states what's the probability a node should be dropped during a training step.

A new vector, $\mathbf{v}$, with the same size as the activation vector $\mathbf{a}$, is created with random values, where each element is sampled from a uniform distribution in the range $[0,1]$.

Then, $\mathbf{v}$ is converted into a **MASK VECTOR** using the rule defined below. This mask is essentially a series of on/off switches for the neurons.

$$
v_i := 
\begin{cases} 
    0 & \text{if the random number} < p \text{ (drop the node)} \\
    1 & \text{if the random number} \ge p \text{ (keep the node)}
\end{cases}
$$

This creates a binary mask that looks something like `[0, 1, 0, 1, 1, ...]`.

An **element-wise product** ($\odot$) is then performed between the activation vector $\mathbf{a}$ and this mask vector $\mathbf{v}$. This step effectively zeroes out the activations for the nodes that were selected to be dropped.

$$\mathbf{a}_{\text{dropped}} := \mathbf{a} \odot \mathbf{v}$$

Then after training, during the inference process, the activations are scaled via: $$
\mathbf{a} := \mathbf{a} \odot{(1-p)}
$$---
### The Mismatch Problem

In this classic implementation of dropout, there's a fundamental mismatch between what happens during training and what happens during inference.

#### During Training

Let's say you have a dropout probability of `p = 0.4` (a 40% chance of a neuron being dropped). This means, on average, only **60%** of the neurons in a layer are active and passing their output forward. The total output of the layer is therefore, on average, only 60% of its potential maximum.

#### During Inference (Prediction)

During inference, dropout is **turned off**. All neurons are active (100% of them). If you do nothing, the layer's output will now be significantly larger than what it was, on average, during training. This sudden change in magnitude can lead to inaccurate predictions because the model was trained with smaller activation values.

---
#####  The Solution: Scaling at Inference Time

To fix this, you have to make the inference phase behave like the training phase.

By scaling the activations at inference time via $\mathbf{a} := \mathbf{a} \odot{(1-p)}$, you are manually reducing the layer's output to match the smaller, "dropped-out" scale the model learned to expect during training.

Using our example with `p = 0.4`, you would multiply all activations by `(1 - 0.4) = 0.6`. This scales the output down by 40%, making it consistent with the average output seen during training.

---
## Dropout - Co-Adaptation Interpretation

Why does Dropout work well?

* Network will learn not to rely on particular connections too heavily
* Thus, will consider more connections (because it cannot rely on individual ones)
* The weight values will be more spread-out (may lead to smaller weights like with L2 norm)
* Side note: You can certainly use different dropout probabilities in different layers (assigning them proportional to the number of units in a layer is not a bad idea, for example)



---
# References

Hinton, G. E., Srivastava, N., Krizhevsky, A., Sutskever, I., & Salakhutdinov, R. (2012).
Improving neural networks by preventing co-adaptation of feature detectors. arXIv
preprint arXiv:1207.0580.

Srivastava, N., Hinton, G., Krizhevsky, A., Sutskever, I., & Salakhutdinov, R. (2014).
Dropout: a simple way to prevent neural networks from overfitting. The Journal of
Machine Learning Research, 15(1), 1929-1958.

