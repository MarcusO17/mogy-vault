Created : 2025-10-24 11:16
Tags :
Type :

---
# Convolutional Neural Networks

CNN has a different [[Multilayer Networks|Relational Inductive Bias]]. Unlike MLP's which focus on independence, CNN's has Locality. So the CNN's is able to capture an "area" spatial, data.

---
## The First "Published" CNN

The first CNN was published by Yann LeCunn and Co-Authors in 1989. It's was called LeNet-5.
The paper can be accessed below :
[Backpropagation Applied to Handwritten Zip Code Recognition | MIT Press Journals & Magazine | IEEE Xplore](https://ieeexplore.ieee.org/document/6795724)

Later in 2002, Yann LeCunn and Co-authors republished their LeNet-5 architecture [Gradient-based learning applied to document recognition | IEEE Journals & Magazine | IEEE Xplore](https://ieeexplore.ieee.org/document/726791)

---
## Le-Net 5

![[Pasted image 20251028194139.png]]


![[Pasted image 20251024131414.png]]

![[LeNet-5_architecture.svg]]



---
## Weight Sharing

The kernel slides over the input to generate a feature map.  
At each position, it looks at a small region of the input — called the **receptive field**.  
That receptive field is then **condensed into one unit** by taking the weighted sum of all the values inside it:

$$
y = \sum_{j=1}^{g} w_j x_j + b  
$$

Here, $x_j$ are the input values, $w_{j}$ are the kernel weights, and $b$ is an optional bias term.  
Each kernel uses **the same weights** across the entire input — this is called **weight sharing**.  
As the kernel moves across the image, it captures local patterns (like edges or textures) that form the **feature map**.

We can also use multiple kernels of varying weights to create different feature maps.

### Backpropagation in CNN's

Is it essentially the same, multivariable chain rule but now with weight sharing.
Since the $w$s are on the kernel, $$
w_{1} := w_{2} := w_{1} - \eta \cdot \frac{1}{2}\left( \frac{ \partial \mathcal{L} }{ \partial w_{1} } +\frac{ \partial \mathcal{L} }{ \partial w_{2} }   \right)
$$

---
## Size of Convolution Operations

So what sizes are my feature maps if my kernel is 5x5 on a input size of 32x32?
This can be calculated using:
$$
O=\frac{W-K+2P}{S} +1
$$
Where :
* O is the output width
* W is the input width
* K is the kernel width
* P is padding
* S is stride
	* Stride is how many pixels/units is the kernel being moved per operation/capture. This is usually 1?

So a 32 - 5 + 1 is 28x28 size.

---
## CNN Issues
CNNs are invariant to slight translation (shifting) because the convolution operation is equivariant and the pooling layer provides tolerance. However, they are not naturally invariant to scale or rotation, and require techniques like data augmentation or specialized architectures to learn these properties.

![[Pasted image 20251029133719.png]]

---
## How to Deal with Local Invariance

![[Pasted image 20251029134005.png]]

The main point of pooling (usually Max Pooling) in a CNN is to serve two critical functions: 

Pooling achieves dimensionality reduction by systematically downsampling the feature maps (e.g., reducing a $4 \times 4$ area to $2 \times 2$), which dramatically cuts down the computational load and memory usage for the subsequent layers, making the network faster and more feasible to train.

Simultaneously, it achieves local translation invariance by only keeping the single strongest feature (the maximum value) within a small region. This makes the network robust, as it learns to focus on the general presence of a feature (like an edge or a curve) rather than its exact, fragile pixel location, ensuring that a **slightly** shifted object is still correctly recognized.

This still doesn't deal with massive translations.


---
# References


