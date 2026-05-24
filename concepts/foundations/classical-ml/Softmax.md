Created : 2025-09-09 10:31
Tags :
Type :
Lecture : #L08
Video : https://www.youtube.com/watch?v=10PTpRRpRk0

---
# Softmax

## Before Softmax...

In [[Logistic Regression]] we can see that, since it uses a single [[Sigmoid Function|sigmoid function]] as it's activation layer, it only allows binary classification. How can we try multiclass-classification?

![[Pasted image 20250909135856.png]]

To combat this, we can compile multiple sigmoid nodes for $n$, number of classes and assign weights $w_{1,1},w_{1,2},w_{2,1},w_{k,m}$ from each input $x_{1},x_{2},\dots,x_{n}$, to let each sigmoid node provide a $P(x)$ for each class for each input. This is also known as the *[[One-vs-Rest Classification|One-vs-Rest]]* approach. To get the class, the sigmoid outputting highest probability is taken.

---
## Multinomial Logistic Regression

![[Pasted image 20250909142556.png]]

To perform multiclass logistic regression, we use the softmax activation function instead of multiple sigmoid nodes. Unlike sigmoid, where each node's output is independent, softmax takes all the net inputs for a given data point simultaneously. This produces a probability distribution over the classes, where the output values are all non-negative and sum to 1.0.

For instance, if we have three classes, softmax might output:

$$\text{Softmax Output}=[0.02,0.05,0.93]$$

To make a final prediction, we apply the *argmax* function to this output vector. Argmax finds the index of the largest value, which corresponds to the predicted class. In the example above, the largest value is 0.93, which is at the third index. Therefore, the model's prediction is the third class.



---
## Softmax Function

Softmax can be defined as:
$$
P(y=t|z_{t}^{[i]}) = \sigma_{\text{softmax}}(z_{t}^{[i]})= \frac{e^{z_{y}^{[i]}}}{\sum_{j=1}^{h}e^{z_{j}^{[i]}}}
$$
where:
$$
t \in \{1,\dots ,h\}
$$
						 $h$ is the number of class labels.



$t$ will be the target class for this example. Hence, we want to find the probability of class $t$ being the target class based on the logits $z$, at the $[i]$-th training example.

There will be $h$ number of logits/net inputs. At each $[i]$-th training example, there will be $h$ different logits as their weights (as $w_{i,1},w_{i,2},\dots,w_{i,h}$) will vary. They are then run through the exponential function $e^z$.

$\sum_{j=1}^{h}e^{z_{j}^{[i]}}$ is the *normalization* term. a variable j, sums all of the exponential $h$ values. By dividing $e^{z_{j}^{[i]}}$ by it's total sum. We can get interpret them as probabilities, as their value will be between 0 to 1.

>[!note]- Normalization Term
> A true probability distribution must satisfy two conditions:
>- Every value must be between 0 and 1.
>- The sum of all values must equal 1.
>The $e^z$ , helps to ensure all values are positive (as probabilities cannot be -ve). $\sum_{j=1}^{h}e^{z_{j}^{[i]}}$ then ensures the values are scaled to range.






---
# References


