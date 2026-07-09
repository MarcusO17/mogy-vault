---
created: 2025-08-09
type: source
source-type: paper
status: draft
topic: ML
---

# ImageNet Classification with Deep Convolutional Neural Networks

## Raw notes

### Dataset & Data Processing
- Images down-sampled to a fixed resolution of $256 \times 256$ (rescaled shorter side to 256, cropped central $256 \times 256$ patch).
- The only preprocessing applied was subtracting the mean RGB value over the training set from each pixel (training on centered raw RGB values).

### Key Techniques
- **ReLU Nonlinearity**: Used for training acceleration (reaches 25% training error rate much faster than tanh).
- **Local Response Normalization (LRN)**: Applied after ReLU in certain layers to aid generalization (acting as a brightness normalization scheme with hyperparameters $k = 2$, $n = 5$, $\alpha = 10^{-4}$, and $\beta = 0.75$).
- **Overlapping Pooling**: Max pooling with window size $z = 3$ and stride $s = 2$ (overlapping since $s < z$). Helps reduce overfitting slightly compared to non-overlapping pooling of the same output dimension.
- **Data Augmentation**: 
  1. Generating image translations and horizontal reflections (extracting random $224 \times 224$ patches). At test time, averages predictions on 10 patches (4 corners, center, plus their horizontal reflections).
  2. Altering RGB intensities using PCA on the ImageNet training set. Multiples of principal components (eigenvectors and eigenvalues scaled by a Gaussian random variable) are added to each image pixel. Captures invariance to illumination intensity and color changes.
- **Dropout**: Applied in the first two fully-connected layers (probability 0.5) to reduce co-adaptation of neurons and force the network to learn more robust features. At test time, neural outputs are scaled by 0.5.

## Key concepts mentioned
- [[ReLU Function]]
- [[Local Response Normalisation]]
- [[Dropout]]
- [[Data Augmentation]]
- [[Overfitting]]

*From* → Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton (2012)
