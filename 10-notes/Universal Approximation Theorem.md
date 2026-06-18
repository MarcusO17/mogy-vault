---
created: "2026-06-18"
type: note
status: draft
topic:
---

# Universal Approximation Theorem




The Universal Approximation Theorem states that an [[Multilayer Perceptron|MLP]] with a wide layer singular hidden layer can approximate any continuous function to any desired degree of accuracy.

So with the existence Universal Approximation Theorem? Why do we want to use deeper architectures?

For traditional MLPs, you don't go deeper than 1 or 2 layers in practice as there will be due to [[Vanishing Gradients|vanishing]]/[[Exploding Gradients|exploding gradients]] problems. While implementing traditional MLPs with 3 or 4 layers, it doesn't train so well anymore as the [[Backpropagation|backpropagation]] does not go back too far.




*From* →