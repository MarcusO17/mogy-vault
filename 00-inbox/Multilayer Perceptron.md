  Created : 2025-09-14 12:22
Tags :
Type :
Lecture : #L09
Video : https://www.youtube.com/watch?v=jD6IKpqSJM4

---
# Multilayer Perceptron



---



---
## Issues with Activations + Loss Functions 

[[Sigmoid Function]] + [[Mean Squared Error|MSE Loss]] has the problem of very flat gradients when the output is very wrong. This causes a phenomenon we like to call [[Logistic Regression#Logistic Regression Learning Rule|Vanishing Gradients]]


### Flat Gradients
During Gradient Descent, updates to weights are stored in $\Delta w = -\eta \cdot \frac{\partial L}{\partial w}$, which is then added to the weights (depends on Online, Batch, and Minibatch Mode). The chain rule breaks this down:
$$\frac{\partial L}{\partial w} = \underbrace{\frac{\partial L}{\partial \hat{y}}}_{\text{loss}} \cdot \underbrace{\frac{\partial \hat{y}}{\partial z}}_{\text{activation}} \cdot \underbrace{\frac{\partial z}{\partial w}}_{x}$$
where $z = w \cdot x + b$ is the pre-activation, $\hat{y} = \sigma(z)$ is the post-activation, and $\frac{\partial L}{\partial \hat{y}}$ is analytically defined by our choice of loss function. Let's see how certain gradient issues can arise from this.

In the case of MSE loss, $\frac{\partial L}{\partial \hat{y}} = (\hat{y} - y)$, which is large when the prediction is very wrong (e.g., $\hat{y} \approx 0$ and $y = 1$). So it does represent it's large error difference and will then be reflected in the $\Delta w$ right? right? Let's keep looking.

[[Sigmoid Function\|Sigmoid's]] derivative $\frac{\partial \hat{y}}{\partial z} = \sigma(z)(1 - \sigma(z))$ maxes at $0.25$ (when $\hat{y} = 0.5$) (Feel free to check [[Logistic Regression#Logistic Regression Learning Rule| the derivative graph of a sigmoid]]) and drops to near $0$ when saturated ($\hat{y} \approx 0$ or $1$). When the prediction is very wrong, $z$ is pushed to extremes (very positive/negative), which is exactly when sigmoid saturates and its derivative goes near $0$.

So even with a large MSE error, the overall gradient $\frac{\partial L}{\partial w}$ collapses as it will be multiplied by near-zero $\sigma'(z)$, the weights then barely update. In deeper networks this gets worse, as gradients are multiplied through many chain rule terms before reaching early weights, shrinking further each layer. This is the **Vanishing Gradient** problem.










---
# References


