Created : 2025-08-24 17:31
Tags :
Type :
Lecture : #L08
Video : https://www.youtube.com/watch?v=10PTpRRpRk0

---
# Logistic Regression

Logistic Regression uses the [[Sigmoid Function|logistic sigmoid]] which effective transforms regression into a classifier of binary classes {1,0}.
$$
\sigma(z) = \frac{1}{1+e^{-z}}
$$

Very similar to [[ADALINE]] but this time the threshold function is no longer an identity function, as well a different loss function.

![[Pasted image 20250825194408.png]]

$$
	\underbrace{\mathbf{w}^T \mathbf{x} + b}_{\text{logit } z} \xrightarrow{\sigma} \underbrace{h(\mathbf{x})}_{\text{probability}} \xrightarrow{\text{threshold at } 0.5} \underbrace{\hat{y}}_{\text{class label}}
$$

This effectively uses the perceptron? (I am not too sure what to call the earlier layers + input) to  acquire logits (regular linear outputs) and converts them into probabilities using the sigmoid function . We can then kind of apply the acquired probas under a threshold function into either upper boundary, $1$ or lower boundary, $0$


Given that:
$$
h(\mathbf{x}) = \sigma(\mathbf{w}^T  \mathbf{x} + b)
$$
We compute the posterior (the probability of the class label, $y$ given feature vector, $\mathbf{x}$):
$y = \text{class label}$
$\mathbf{x} = \text{feature vector}$
$$
P(y|\mathbf{x})=\begin{cases}
h(\mathbf{x}) \quad  &\text{if y = 1} \\
1-h(x) \quad  &\text{if y  = 0}
\end{cases}
$$
For a binary class problem, we want these probas to be:

$$
	\begin{align}
	P(y=0|\mathbf{x}) 
	\end{align}
$$


---
## Logistic Regression Loss Function

Logistic Regression uses the Likelihood Loss Function.

For logistic regression, we want to maximise the $\dots$ ($\downarrow$, is the Maximum Likelihood Estimation)
$$
P(y^{[i]},\dots,y^{[n]}|\mathbf{x}^{[i]},\dots,\mathbf{x}^{[n]}) = \prod^n_{i=1}P(y^{[i]}|\mathbf{x}^{[i]}).
$$

In practice, we can also try to maximise the natural log of that equation which is known as the log-likelihood function.

To be more convenient, we could minimise the **[[Cross Entropy|negative log-likelihood]]** instead of the maximising the function, allowing to still perform gradient descent instead of gradient ascent.

![[Cross Entropy#Binary Cross-Entropy]]


---
## Logistic Regression Learning Rule

![[Pasted image 20250826134756.png]]

The edges of $\frac{d}{dz}\sigma(z)$ show plateauing, indicating slow gradient changes. Hence, $z$ values that fall into these edge regions will:

- **Experience [[Vanishing Gradients|vanishing gradients]]** - weight updates become extremely small  
- **Slow learning progress** - neurons in saturation zones learn minimally  
- **Risk getting stuck** - network may stop improving in affected regions  
- **Weaken signal propagation** - subsequent layers receive diminished gradients  

This saturation effect is why deep networks with sigmoid activations often suffer from the **[[Vanishing Gradients|vanishing gradient problem]]**.

---
Same gradient descent rule as before,

$$
\frac{ \partial \mathcal{L} }{ \partial w_{j} } =\frac{ \partial \mathcal{L} }{ \partial a } \cdot \frac{ \partial a }{ \partial z } \cdot \frac{ \partial z }{ \partial w_{j} }
$$
Where:
* $\mathcal{L}$ , loss
* $a$, activation function
* $z$, net input
* $w_j$, weight
---


---
# References


