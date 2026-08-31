---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/architecture/cnn
---

# Convolutional Neural Networks

**Convolutional Neural Networks** (CNNs) are a class of deep neural networks designed for processing grid-structured data, such as images. 

Unlike Multilayer Perceptrons (MLPs), which assume feature independence, CNNs introduce specific **relational inductive biases** suitable for spatial data:
- **Locality**: Assumes that nearby pixels are highly correlated and form meaningful local patterns.
- **Translation Equivariance**: Assumes that a feature (e.g., an edge) is equally useful regardless of its position in the image. This is achieved through **weight sharing**.

---

## Core Components

### 1. The Convolution Operation & Weight Sharing
A kernel (or filter) slides across the input to generate a **feature map**. At each step, it computes the weighted sum over a local **receptive field**:

$$
y = \sum_{j=1}^{g} w_j x_j + b
$$

where $x_j$ are the input pixel values in the receptive field, $w_j$ are the kernel weights, and $b$ is the bias.
Because the same kernel weights are reused across the entire input, this drastically reduces the parameter count compared to fully-connected layers.

#### Output Size Calculation
The spatial dimensions of the output feature map can be calculated using:
$$
O = \frac{W - K + 2P}{S} + 1
$$
- $O$: Output width/height
- $W$: Input width/height
- $K$: Kernel size
- $P$: Padding size
- $S$: Stride size

### 2. Pooling Layers
Pooling layers (most commonly **Max Pooling**) downsample the feature maps to serve two functions:
- **Dimensionality Reduction**: Shrinks the spatial size of the representation, reducing the computational load and parameter count for subsequent layers.
- **Local Translation Invariance**: By selecting only the maximum activation value in a region, the network becomes robust to small translations (shifts) of features.

---

## Backpropagation with Weight Sharing
In CNNs, backpropagation follows the multivariable chain rule, but since weights are shared across multiple spatial locations, the gradients are accumulated. Specifically, the gradient of the loss $\mathcal{L}$ with respect to a shared kernel weight $w_j$ is the sum of the gradients from all receptive fields where $w_j$ was applied:

$$
\frac{\partial \mathcal{L}}{\partial w_j} = \sum_{i} \frac{\partial \mathcal{L}}{\partial y_i} \cdot \frac{\partial y_i}{\partial w_j}
$$

---

## Historical Context: LeNet-5
LeNet-5, developed by Yann LeCun and colleagues in 1989 and refined in 1998, was the first widely successful CNN architecture. It was primarily used for handwritten digit recognition (e.g., zip codes and bank checks).

![[LeNet-5_architecture.svg]]

---
*From* → [[Multilayer Networks]]
