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
	P(y=0|\mathbf{x})  &\approx 1 \quad \text{if } y= 0 \\
	P(y=1|\mathbf{x})  &= 1- P(y=0|\mathbf{x}) \quad \text{if } y = 1
	\end{align}
$$
Simply means, if the true label, $y$ is 0 then probability of the true answer, where $y$ is 0 should be very high $(\approx / \to 1)$ , vice versa. 

We use 1 - P as the sum rule of probabilities states that probabilities and their complement case must sum to 1.

So when y is 1, we kinda wanna see $P \approx 0.99$ or smtg, while y is 0, $P \approx 0.01$ as $h(\mathbf{x})$ here only computes probabilities of a case and the complement must be computed.

---
## Logistic Regression Loss Function
### Likelihood Loss Function

Logistic Regression uses the Likelihood Loss Function.

For logistic regression, we want to maximise the $\dots$ ($\downarrow$, is the Maximum Likelihood Estimation) by finding good/optimal parameters
$$
P(y^{[i]},\dots,y^{[n]}|\mathbf{x}^{[i]},\dots,\mathbf{x}^{[n]}) = \prod^n_{i=1}P(y^{[i]}|\mathbf{x}^{[i]}).
$$
MLE here shows us that for each inferred set, we compute the product of all probabilities across a certain class label, almost like:
$$
	P(\text{all three outcomes}) = P(\text{flip 1}) \times P(\text{flip 2}) \times P(\text{flip 3})
$$

Hence the final outcome of a test set being a certain class depends of all of it's observed dataset examples probabilities of it being the true class. 

The Maximum Likelihood Estimation is also represented by:
$$
	\mathcal{L}(\mathbf{w}) = \prod^n_{i=1} P(y^{[i]}|\mathbf{x}^{[i]})
$$
The ~~**LIKELIHOOD** (not loss..)~~  error of the weights of the model can be computed by MLE, alike to SSE for Linear Regression.

MLE would appreciate a maximum. (A higher value) $\approx 1$ would indicate a better result. Let's assume that the individual probabilities of the observed dataset points are high.. 
$$
	\text{error} = 0.9 \times 0.89 \times 0.9
9 \times \dots$$

We would achieve a $\mathcal{L}(\mathbf{w})$ that is $\approx$ 1, the Likelihood is maximized which is not too helpful for gradient descent, where we take, (check [[Online, Batch, and Minibatch Mode]])
$$
	w←w+η∇L(w)
$$
that would mean we are looking for **gradient ascent**, and it's weird and unconventional, so instead we just negate the formula to, 
$$
-\mathcal{L}(\mathbf{w}) = -\prod^n_{i=1} P(y^{[i]}|\mathbf{x}^{[i]})
$$


Another issue pops up if we observe a bad batch where, 
$$
	\text{error} = 0.01 \times 0.3 \times 0.09 \times \dots
$$
The loss of the batch would be tiny, perhaps $0.00003$ and over a dataset where, $n \geq 100000$ we can see the opportunity of a numerical underflow.

---
### Log Likelihood

Hence we take advantage of the log rule where,
$$
	 \log(a \times b \times c) =  \log(a) + \log(b) + \log(c)
$$
We effectively get rid of the multiplication inside MLE, turning it into, 
$$
	\begin{align}
		-\mathcal{L}(\mathbf{w})  &= -\prod^n_{i=1} P(y^{[i]}|\mathbf{x}^{[i]}) \\
		-\mathcal{L}(\mathbf{w})  &= -\sum^n_{1=i} \log  P(y^{[i]}|\mathbf{x}^{[i]}) \\
	\end{align}
$$
 With addition it would nearly eradicate the previous issue of the numerical underflow. Bringing to the rise of the logistic regression loss function. Negative Log-Likelihood.

---

Before we can get into cross entropy, we need to understand **Bernoulli's distribution**, basically the sum of probabilities rule. 

**Bernoulli's Distribution**
$$
	 P(y|\mathbf{x}) = a^{y}(1-a)^{(1-y)}
$$
It's literally $\downarrow$ rewritten (defined not derived) as 1 liner using exponent rules, 
$$
	P(y \mid \mathbf{x}) = \begin{cases} h(\mathbf{x}) & \text{if } y = 1 \\ 1 - h(\mathbf{x}) & \text{if } y = 0 \end{cases}
$$

Since $y \in \{0, 1\}$, the exponents act as an on/off switch:

$$P(y \mid \mathbf{x}) = h(\mathbf{x})^y \cdot (1 - h(\mathbf{x}))^{1-y}$$

When $y = 1$, the right term cancels since $(1-h(\mathbf{x}))^{0} = 1$, leaving $h(\mathbf{x})$.

When $y = 0$, the left term cancels since $h(\mathbf{x})^{0} = 1$, leaving $1 - h(\mathbf{x})$.

---



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


