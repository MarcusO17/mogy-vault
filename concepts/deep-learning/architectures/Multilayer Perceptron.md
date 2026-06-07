  Created : 2025-09-14 12:22
Tags :
Type :
Lecture : #L09
Video : https://www.youtube.com/watch?v=jD6IKpqSJM4

---
# Multilayer Perceptron

The multilayer perceptron are [[Fully Connected Layer|fully connected]] feedforward neural networks with one or more **hidden layers** .Similarly to [[Multilayer Networks]].

![[Pasted image 20250914122516.png]]

Let's do a quick recap of the how do we backpropagate in the Multi-Layer Perceptron. Let's take $w^{(1)}_{1,1}$ for example...
$$
\begin{align}
    \frac{ \partial l }{ \partial w^{(1)}_{1,1} } & = \overbrace{\frac{ \partial l }{ \partial o } \cdot \frac{ \partial o }{ \partial a^{(2)}_{1} } \cdot \frac{ \partial a^{(2)}_{1} }{ \partial a^{(1)}_{1} } \cdot \frac{ \partial a^{(1)}_{1} }{ \partial w^{(1)}_{1,1} }}^{\text{Path 1}} \\
    & \quad + \overbrace{\frac{ \partial l }{ \partial o } \cdot \frac{ \partial o }{ \partial a^{(2)}_{2} } \cdot \frac{ \partial a^{(2)}_{2} }{ \partial a^{(1)}_{1} } \cdot \frac{ \partial a^{(1)}_{1} }{ \partial w^{(1)}_{1,1} }}^{\text{Path 2}}
\end{align}
$$

---

In Multilayer Perceptrons, Loss is NO LONGER convex. This is why[[Understanding Gradient Descent|gradient-based optimization]]] can find different solutions. In [[Linear Regression]], [[ADALINE]], [[Logistic Regression]], and [[Softmax|Softmax Regression]] , their loss functions are usually convex, but that is no longer the case with MLPs.

![[Pasted image 20250914123843.png]]

By starting with random weights, we can reach different local minima, hence it's pretty good practice.

---
## Issues with Activations + Loss Functions 

[[Sigmoid Function]] + [[Mean Squared Error|MSE Loss]] has the problem of very flat gradients when the output is very wrong. (Causes [[Logistic Regression#Logistic Regression Learning Rule|Vanishing Gradients]])

### Flat Gradients

During[[Understanding Gradient Descent|gradient descent]]], updates to weights happen via $\Delta w = -\eta \cdot \frac{\partial L}{\partial w}$. The chain rule breaks this down: $\frac{\partial L}{\partial w} = \frac{\partial L}{\partial \hat{y}} \cdot \frac{\partial \hat{y}}{\partial z} \cdot \frac{\partial z}{\partial w}$, where $z = w \cdot x + b$ is the pre-activation. 

- For MSE loss, $\frac{\partial L}{\partial \hat{y}} = (\hat{y} - y)$, which can be large if the prediction is very wrong (e.g., $\hat{y} \approx 0$ and $y=1$). 

- But [[Sigmoid Function|sigmoid's]] derivative $\frac{\partial \hat{y}}{\partial z} = \sigma(z)(1 - \sigma(z))$ maxes at 0.25 (when $\hat{y}=0.5$) and drops to near 0 when saturated ($\hat{y} \approx 0$ or $1$). 

- $\frac{\partial z}{\partial w} = x$, usually fine. When the output is very wrong, $z$ goes to extremes (very positive/negative), saturating sigmoid and making its derivative tiny. This is a classic example of [[Vanishing Gradients]].
  Even with a large error from MSE, the overall gradient flattens out—multiplied by near-zero $\sigma'(z)$, so weights barely update. This stalls learning, especially since gradients * weights (through the chain) get killed before reaching $w$. 

In short, when $\hat{y}$ hits 0 or 1 (saturated, often wrong), gradients change to basically 0, trapping the model.










---
# References


