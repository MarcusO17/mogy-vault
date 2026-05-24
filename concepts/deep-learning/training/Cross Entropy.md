Created : 2025-09-09 15:42
Tags : #LossFunctions #Classification #LogisticRegression 
Type : Concept
Lecture : #L08
Video : https://www.youtube.com/watch?v=10PTpRRpRk0

---
# Cross Entropy

 Cross Entropy is a loss function used to measure the performance of a classification model. It quantifies the difference between the model's predicted probability distribution and the true distribution of the labels. It tells you how "wrong" your model is.
## Binary Cross-Entropy

$$
H_{a}(\mathbf{y})=-y^{[i]}\log(\sigma(z^{[i]})) + (1-y^{[i]})\log(1-\sigma(z^{[i]}))
$$

BCE is also used in binary-class [[Logistic Regression]] as its [[Loss Functions|loss function]], aka [[Maximum Likelihood Estimation|Negative log-likelihood]].
Hence the loss function (at each i) would be:

$$
\mathcal{L}(\mathbf{w})=-y^{[i]}\log(\sigma(z^{[i]})) + (1-y^{[i]})\log(1-\sigma(z^{[i]}))
$$
>[!note] Why?
>- It measures how well the predicted probabilities $\hat{y}^{[i]}$ match the true labels $y^{[i]}$ .
>- If $y^{(i)} = 1$ we want $\hat{y}^{[i]}$ to be close to 1 (so $-\log(\hat{y}^{(i)})$ is small). 
>- If $y^{(i)} = 0$ we want $\hat{y}^{[i]}$ to be close to 0 (so $-\log(1 - \hat{y}^{(i)})$ is small). 


## Categorical Cross-Entropy

Multi-Category Cross Entropy:
$$
H_{a}(\mathbf{y}) = \sum_{i=1}^{n}\sum_{j=1}^{K}-y_{j}^{[i]}\log(a_{j}^{[i]}) 
$$
- which assumes, $y_j^{[i]}$ is [[One-Hot Encoding|one-hot encoded]], either 1 or 0.
- $H_a(\mathbf{y})$ - is the CCE across all training examples.

Firstly, the equation runs a nested sum, across all training examples $n$ and per-training example, the $-y_{j}^{[i]}\log(a_{j}^{[i]})$ of all classes (probability values).

An important factor is $y_j^{[i]}$ is one hot encoded. $a_{j}^{[i]}$ represents the [[Softmax|activation function]] result/ probability.  

> [!help]- Why Log?
> ## 1. Asymmetry of Penalties
> The logarithm function creates an **asymmetric penalty curve**. 
> ![[Pasted image 20250910093847.png|500,500]]
> The penalty for being confidently wrong is far greater than for being uncertainly wrong.
> -   **Confident and Wrong**: Prediction of $\hat{y}^{(i)}_j = 0.01$ for the correct class → $-\log(0.01) \approx 4.6$ (huge loss).
> -   **Confident and Right**: Prediction of $\hat{y}^{(i)}_j = 0.99$ for the correct class → $-\log(0.99) \approx 0.01$ (minimal loss).
> -   **Uncertain**: Prediction of $\hat{y}^{(i)}_j = 0.5$ → $-\log(0.5) \approx 0.69$ (moderate penalty).
> 
> ## 2. Numerical Stability
> Predicted probabilities can become extremely small numbers (e.g., $10^{-100}$). Multiplying these tiny numbers together repeatedly during training can lead to a condition called **numerical underflow**, where the product becomes so small that the computer treats it as zero, making the training unstable. The logarithm transforms multiplication into addition $-\log(a \cdot b) = -\log(a) + -\log(b)$. Making it much stable
> 
> ## 3. Connection to [[Maximum Log-Likelihood]]
> Minimizing this loss is equivalent to **maximizing the log-likelihood** of the data. The negative logarithm turns this maximization problem into a standard minimization problem for optimizers like gradient descent.

One-hot encoding on $y$ makes it so that it only checks the class that the training example was trying to predict. As one-hot encoding converts them to $\{1,0\}$, The non-related classes loss are zero and only the target class of the $[i]$-th training example is non-zero. That probability is then checked to see how good/bad the prediction was. 

As the log of a value between $0-1$ is always negative, a -ve is added to turn it positive (Since the primary goal was to **MINIMIZE** the loss).
### Example

![[Pasted image 20250910095156.png]]

At the first training example.
![[Pasted image 20250910095250.png]]




---
# References


