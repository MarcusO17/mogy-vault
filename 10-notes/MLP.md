---
created: 2026-06-18
type: note
status: draft
topic: ML
tags:
  - dl/architecture/mlp
  - dl/training/backprop
---

# MLP

The  multilayer perceptron are [[Fully Connected Layer|fully connected]] feedforward neural networks with one or more **hidden layers** .Similarly to [[Multilayer Networks]].

![[Pasted image 20250914122516.png]]

Let's do a quick recap of the how do we backpropagate in the Multi-Layer Perceptron. Let's take $w^{(1)}_{1,1}$ for example...
$$
\begin{align}
    \frac{ \partial l }{ \partial w^{(1)}_{1,1} } & = \overbrace{\frac{ \partial l }{ \partial o } \cdot \frac{ \partial o }{ \partial a^{(2)}_{1} } \cdot \frac{ \partial a^{(2)}_{1} }{ \partial a^{(1)}_{1} } \cdot \frac{ \partial a^{(1)}_{1} }{ \partial w^{(1)}_{1,1} }}^{\text{Path 1}} \\
    & \quad + \overbrace{\frac{ \partial l }{ \partial o } \cdot \frac{ \partial o }{ \partial a^{(2)}_{2} } \cdot \frac{ \partial a^{(2)}_{2} }{ \partial a^{(1)}_{1} } \cdot \frac{ \partial a^{(1)}_{1} }{ \partial w^{(1)}_{1,1} }}^{\text{Path 2}}
\end{align}
$$

We can see clearly that the effects of $w^{(1)}_{1,1}$ are going backwards in a chain of affected outputs back towards it.



*From* →
