---
created: 2026-07-09
type: source
source-type: paper
status: draft
topic: ML
tags:
  - dl/architecture/cnn
---

# Very Deep Convolutional Networks for Large-Scale Image Recognition

* **Authors**: Karen Simonyan & Andrew Zisserman (2014)
* **PDF**: [[1409.1556v6.pdf]]

---

## Raw notes

### Architecture & Small Filters
* Thorough evaluation of networks of increasing depth.
* Uses very small ($3 \times 3$) convolutional filters throughout the entire network, convolved with the input at every pixel (stride 1).
* **Why $3 \times 3$ filters?**
  1. Stacking multiple $3 \times 3$ layers makes the decision function more discriminative (due to intermediate non-linear activations).
  2. Reduces the number of parameters compared to larger filters (e.g., three $3 \times 3$ layers have the same effective receptive field as one $7 \times 7$ layer, but use $(3 \times 3^2 \times C^2) = 27 C^2$ parameters instead of $49 C^2$).

### Normalization
* The paper notes that [[Local Response Normalisation]] (LRN) does not improve performance on the ILSVRC dataset, but instead leads to increased memory consumption and computation time.

---

## Key concepts mentioned
- [[Convolutional Neural Networks]]
- [[Local Response Normalisation]]

*From* → [[Convolutional Neural Networks]]
