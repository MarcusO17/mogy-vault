---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - linear-models
  - optimization
  - pytorch
---

# ADALINE

**ADALINE** (Adaptive Linear Neuron) is an early single-layer artificial neural network architecture developed by Bernard Widrow and Ted Hoff in 1960. 

While visually similar to [[The Perceptron]], ADALINE differs in how its weights are updated during learning:
- **Perceptron**: Weights are updated based on the discrete output of a threshold step function.
- **ADALINE**: Weights are updated based on the continuous output of the linear activation function (the net input) before applying any threshold function.

This formulation makes ADALINE mathematically equivalent to [[Linear Regression]] with an added threshold step function for classification. Because its activation function is linear, the loss function (Mean Squared Error) is convex, guaranteeing that gradient descent can find the global minimum.

### PyTorch Implementation

Below is a standard ADALINE classifier implementation in PyTorch using a linear layer and Mean Squared Error (MSE) loss:

```python
import torch
import torch.nn.functional as F

class Adaline(torch.nn.Module):
    def __init__(self, num_features):
        super().__init__()
        self.linear = torch.nn.Linear(num_features, 1)
        
        # Initialize weights and bias to zero (typical for ADALINE)
        with torch.no_grad():
            self.linear.weight.zero_()
            self.linear.bias.zero_()
        
    def forward(self, x):
        # Continuous output (linear activation)
        return self.linear(x).view(-1)

def train_adaline(model, x, y, num_epochs, learning_rate=0.01, seed=123, minibatch_size=10):
    torch.manual_seed(seed)
    optimizer = torch.optim.SGD(model.parameters(), lr=learning_rate)
    cost = []
    
    for epoch in range(num_epochs):
        # Shuffle dataset indices
        shuffle_idx = torch.randperm(y.size(0), dtype=torch.long)
        minibatches = torch.split(shuffle_idx, minibatch_size)
        
        for minibatch_idx in minibatches:
            y_hat = model(x[minibatch_idx])
            loss = F.mse_loss(y_hat, y[minibatch_idx])
            
            optimizer.zero_grad()
            loss.backward()
            optimizer.step()
            
        with torch.no_grad():
            y_hat_all = model(x)
            current_loss = F.mse_loss(y_hat_all, y)
            cost.append(current_loss.item())
            
    return cost
```

*From* → [[Understanding Gradient Descent]]
