---
created: 2026-07-09
type: note
status: draft
topic: ML
tags:
  - dl/stack/pytorch
---

# PyTorch Quick Reference

This is a quick reference and boilerplate template for setting up and training a neural network model in PyTorch.

---

## 1. Imports
```python
import torch
import torch.nn as nn
import torch.nn.functional as F
from torch.utils.data import DataLoader, Dataset
```

## 2. Globals & Hyperparameters
```python
# Device Configuration
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")

# Hyperparameters
RANDOM_SEED = 123
LEARNING_RATE = 0.001
NUM_EPOCHS = 10
BATCH_SIZE = 64

# Network Architecture
NUM_FEATURES = 784
NUM_CLASSES = 10
```

## 3. Model Architecture Template
Define a custom model by subclassing `torch.nn.Module`:

```python
class MLP(nn.Module):
    def __init__(self, num_features, num_classes):
        super().__init__()
        
        # Layer Definitions
        self.linear_1 = nn.Linear(num_features, 128)
        self.linear_2 = nn.Linear(128, num_classes)
        
        # Optional: Weight Initialization Override
        # (Standard layers are initialized automatically, but you can override them)
        nn.init.kaiming_normal_(self.linear_1.weight, nonlinearity='relu')
        if self.linear_1.bias is not None:
            nn.init.zeros_(self.linear_1.bias)
            
        nn.init.xavier_uniform_(self.linear_2.weight)
        if self.linear_2.bias is not None:
            nn.init.zeros_(self.linear_2.bias)

    def forward(self, x):
        # Define the forward pass
        out = self.linear_1(x)
        out = F.relu(out)
        logits = self.linear_2(out)
        return logits
```

---
*From* → [[the PyTorch Process]]
