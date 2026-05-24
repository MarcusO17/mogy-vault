Created : 2025-10-21 14:57
Tags :
Type :
Lecture : L11
Video : https://www.youtube.com/watch?v=xk6qb2IePaE

---
# Kaiming He Initialization

Similar to [[Xiaver Glorot Initialization]], He Initialization is more fit for ReLU


He (or Kaiming) initialization is a weight initialization method designed for neural networks that use **ReLU** or **ReLU-like** activation functions. It ensures that the variance of activations remains stable as signals propagate through layers, preventing vanishing or exploding activations during training.

#### Formula

For a layer with $( m_{in} )$ input units:

$$
W^{(l)} \sim \mathcal{N}\left(0, \frac{2}{m_{in}}\right)  
$$

For a uniform distribution, an equivalent form is:

$$W^{(l)} \sim \mathcal{U}\left(-\sqrt{\frac{6}{m_{in}}}, \sqrt{\frac{6}{m_{in}}}\right)  $$

#### Intuition

ReLU activation functions set all negative inputs to zero, meaning that on average **only half of the neurons are active** at a given time. This causes the output variance of a layer to be roughly **half** the variance of its input. If this reduction in variance continues through many layers, the signal becomes smaller and smaller—eventually vanishing.

He initialization corrects this by **increasing the initial weight variance**. Specifically, it multiplies the variance by 2 (or equivalently, scales the weights by ( \sqrt{2/m_{in}} )) so that after the ReLU zeros out half the values, the remaining activations still preserve the same overall variance as the input. In simple terms: **ReLU halves the signal; He initialization doubles the weight variance to balance it.**

This scaling ensures that both forward activations and backward gradients maintain a stable distribution across deep layers. Without it, the network’s activations would diminish or explode, making training inefficient or unstable.

---
# References


Kaiming He, Xiangyu Zhang, Shaoqing Ren, and Jian Sun. _“Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification.”_ Proceedings of the IEEE International Conference on Computer Vision (ICCV), 2015. arXiv:1502.01852