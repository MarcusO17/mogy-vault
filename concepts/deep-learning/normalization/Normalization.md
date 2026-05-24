Created : 2025-10-15 12:10
Tags :
Type :
Lecture : L11
Video : https://www.youtube.com/watch?v=xk6qb2IePaE

---
# Normalization

## Input Normalization

![[Pasted image 20251015123435.png]]

Since we are using the same learning rate, certain features' weights will be updated too slowly, while others are updated too quickly. So to combat this, we can normalize the inputs using z-score or min-max methods.

But something to think about is ...

>[!question] Normalizing the inputs to the network only affects the *first hidden layer*. What about the other hidden layers?

---
## BatchNorm 

The issue of only the first hidden layer being exposed to normalization effects is solved using BatchNorm.

Batch Normalization (BatchNorm), normalizes the hidden layer inputs as well. This helps with [[Exploding Gradients]]/[[Vanishing Gradients]] problems. It can help increase training stability and convergence rate which means the model's train faster.

---
### How BatchNorm Works?

Suppose, we have the net input $z^{(2)}_{1}$, in the first activation node, at the 2nd hidden layer.

![[Pasted image 20251015125240.png]]

Now, for a single neuron (the 1st neuron in layer 2), let's consider its net input, $z^{(2)}_{1}$ , We will calculate this value for each training example `i` in the minibatch, giving us a set of inputs $z^{(2)}_{1}[i]$, where $i \in \{1,\dots ,n\}$. 

#### BatchNorm Step 1: Normalizing Net Inputs.

$$
\begin{align}
\mu_{j} &= \frac{1}{n} \sum _{i} z^{[i]}_{j} \\
\sigma^{2}_{j} &= \frac{1}{n}\sum_{i}(z_{j}^{[i]} - \mu_{j})^2 \\
z_{j}'^{[i]} &= \frac{z^{[i]}_{j} - \mu_{j}}{\sigma_{j}}
\end{align}
$$

$j$ is the feature index/ previous layer's activations. Then perform z-score standardization.


#### BatchNorm Step 2: Pre-Activation Scaling
$$
\begin{align}
 z^{\prime[i]}_{j} &= \frac{z^{[i]}_{j} -\mu_{j}}{\sqrt{ \sigma^{2}_{j} + \epsilon }} \\
a^{\prime[i]}j &= \gamma_{j} \cdot z^{\prime[i]}_{j} + \beta_{j}
\end{align}
$$
$\gamma$ and $\beta$ are learnable parameter's through backpropagation.
$\gamma$ controls the spread or scale
$\beta$ controls the mean.

Technically, BatchNorm could 'learn' to perform the z-score normalization by itself.


![[Pasted image 20251016214640.png]]

---
### BatchNorm in PyTorch

```python
class MultilayerPerceptron(torch.nn.Module):

	def _init_(self, num_features, num_classes, drop_proba,
				num_hidden_1, num_hidden_2):
		super() ._ init_()
		
		self.my_network = torch.nn. Sequential(
			# 1st hidden layer
			torch.nn. Flatten(),
			torch.nn.Linear(num_features, num_hidden_1, bias=False)
			torch.nn.BatchNorm1d(num_hidden_1),
			torch.nn.ReLU(),
			# 2nd hidden layer
			torch.nn.Linear(num_hidden_1, num_hidden_2, bias=False)
			torch.nn.BatchNorm1d(num_hidden_2),
			torch.nn.ReLU(),
			# output layer
			torch.nn.Linear(num_hidden_2, num_classes)
		)
	
	def forward(self, x):
		logits = self.my_network(x)
		return logits
```
---
### Why BatchNorm Works?

The paper which introduces BatchNorm, mentions about reducing **Internal Covariate Shift**. Internal Covariate Shift is essentially the distribution input shifts/feature shift in the hidden layers which happens overtime during the course of training.

However, there's no guarantee that BatchNorm helps with Internal Covariate Shift. Maybe BatchNorm just provides additional parameters that will help the layers to be more independent.  In the paper, *How does batch normalization help optimization?, (2018)* , instead said it's not about the covariate shift, but BatchNorm makes the optimization landscape much smoother which makes training more stable. This allows faster learning and higher learning rates.

![[Pasted image 20251017095715.png]]

![[Pasted image 20251017100115.png]]

TLDR: 
1. It's not about covariate shift
2. BatchNorm enables faster Convergence by allowing Larger Learning Rates.
3. The good performance of BatchNorm seems unrelated to the Covariate Shift Prevention
--- 
### BatchNorm Variants

| Pre-Activation (Original Version) | Post-Activation (Less Common) |
| :---: | :---: |
| compute net inputs (Z) | compute net inputs (Z) |
| **↓** | **↓** |
| **BatchNorm** | apply activation function (A) |
| **↓** | **↓** |
| apply activation function (A) | **BatchNorm** |
| **↓** | **↓** |
| compute next-layer net inputs | compute next-layer net inputs |

**Note:** **Pre-Activation** is generally the recommended and more common approach.

---
# References

loffe, S., & Szegedy, C. (2015). Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift. In International Conference on Machine Learning (pp. 448-456).

http://proceedings.mlr.press/v37/ioffe15.html

Santurkar, S., Tsipras, D., Ilyas, A. and Madry, A., 2018. How does batch normalization help optimization?. _Advances in neural information processing systems_, _31_.