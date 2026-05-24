Created : 2025-09-24 19:53
Tags :
Type :
Lecture : #L09
Video : https://www.youtube.com/watch?v=jD6IKpqSJM4

---
# Dead Neurons

[[ReLU Function|ReLU]] is probably the most popular [[Activation Functions|activation function]], as it's simple to compute, fast and have good results.

But, ReLU neurons might "die" during training,this is a key consideration in [[Deep Learning|deep networks]]. If the previous inputs are so large/small that the net input is so small that is does not recover. 

[[ReLU Function]]:
$$
f(x) = \text{max}(0,x)
$$

Imagine a neuron $n$ in the 2nd hidden layer. Its input is the weighted sum from the 1st hidden layer. If those previous inputs are all negative (plus bias), then the net input to $n$ is negative for every training example.

Because ReLU outputs zero whenever the input is negative, this neuron will **always output zero.**

Once that happens:

- The gradient through this neuron is also zero (since $\frac{d}{dz}\text{max}(0,z) = 0$ for $z \le 0$) "contributing to the [[Vanishing Gradients]] problem.
- With zero gradient, the weights feeding into this neuron stop updating.
- The neuron is effectively “dead” — it never recovers, because nothing changes its parameters anymore.

>[!important] 
>Dead neurons are not necessarily bad, and can be considered as a form of regularization 


---
## Factors causing Dead Neurons

### 1. **Negative weights or large negative bias**

- Even if the previous layer gives non-negative outputs, a strongly negative weight or bias can push the neuron’s net input below zero for all data.
- Once it’s always negative → output is always zero → gradient is zero → no updates → neuron is dead.

### 2. **High [[Learning Rate|learning rate]]**

- If learning rate is too large, weight updates can “overshoot.”
- A neuron that was active might suddenly be pushed deep into the negative zone, and then never recovers because gradients vanish at $z \le 0$


### 3. **Poor weight initialization**
- If weights are initialized too negatively (or biases are strongly negative), some neurons start out already dead.
- This is why **[[Weight Initialization|He initialization]]** is standard with ReLU — it reduces the chance of early death.








---
# References


