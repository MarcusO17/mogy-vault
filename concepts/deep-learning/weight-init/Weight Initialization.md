Created : 2025-10-17 10:23
Tags :
Type :
Lecture : #L11
Video : https://www.youtube.com/watch?v=xk6qb2IePaE

---
# Weight Initialization

Weight's are preferred to be initialized as small, random numbers to break symmetry.

## Why Weight Initialization?

1. If every weight in a layer is initialized to the same constant value (e.g., all zeros or all ones), every neuron in that layer will compute the exact same function for any given input. Consequently, when the model is trained using backpropagation, every neuron will receive the exact same gradient, leading to identical weight updates. This means the neurons remain identical throughout training, failing to learn diverse or unique features and rendering most of the hidden layer redundant.
   
2. If weights are initialized too large, the output of each layer will grow exponentially (exploding activations), causing inputs (z) to activation functions like $\text{Sigmoid}$ or $\text{Tanh}$ to fall into the saturated regions. For $\text{Sigmoid}$ , this means z becomes too large (e.g., |z| > 4), pushing the output to its asymptotes (0 or 1); for \text{Tanh}, it pushes the output toward -1 or 1 (e.g., |z| > 2.5). 
   ![[Pasted image 20251017145623.png]]
   
   In these saturated regions, the gradient is near zero, leading to the well-known vanishing gradient problem during backpropagation where deep layers receive negligible updates. Conversely, if weights are too small, the output of each layer will shrink exponentially (vanishing activations), keeping z near zero. Although $z \approx 0$ is the non-saturated (steepest) region where the local gradient is strongest, the repeated multiplication of small gradients across many layers in a deep network still leads to a compounded vanishing gradient problem, causing the initial layers to receive negligible updates.


---

## How to initialize Weight

Traditionally, we can initialize weights by sampling from a random uniform 







---
# References


