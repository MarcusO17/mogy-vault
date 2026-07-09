---
created: 2026-07-09
type: note
status: draft
topic: ML
---

# The PyTorch Training Process

This note outlines the standard workflow for loading data, building a model, training it, and evaluating it in PyTorch.

---

## Step 1: Preparation & Settings
Import core libraries, set device configuration, and initialize hyperparameters:

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader
from torchvision import datasets, transforms

# 1. Device configuration
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")

# 2. Hyperparameters
RANDOM_SEED = 42
LEARNING_RATE = 0.001
BATCH_SIZE = 64
NUM_EPOCHS = 10
```

---

## Step 2: Data Loading & Preprocessing
Define input transformations and wrap datasets in PyTorch `DataLoader`s to handle batching, shuffling, and multi-processing:

```python
# 1. Image transformations (example)
custom_transforms = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize((0.5,), (0.5,))
])

# 2. Dataset initialization
train_dataset = datasets.MNIST(root='./data', train=True, transform=custom_transforms, download=True)
test_dataset = datasets.MNIST(root='./data', train=False, transform=custom_transforms)

# 3. DataLoader creation
train_loader = DataLoader(dataset=train_dataset, batch_size=BATCH_SIZE, shuffle=True)
test_loader = DataLoader(dataset=test_dataset, batch_size=BATCH_SIZE, shuffle=False)
```

---

## Step 3: Model, Loss, and Optimizer Initialization
Initialize the random seed, instantiate the model, move it to the target device, and define the loss function and optimizer:

```python
# 1. Set seed for reproducibility
torch.manual_seed(RANDOM_SEED)

# 2. Instantiate and move model
model = MLP(num_features=784, num_classes=10).to(device)

# 3. Define loss and optimizer
criterion = nn.CrossEntropyLoss()
optimizer = optim.Adam(model.parameters(), lr=LEARNING_RATE)
```

---

## Step 4: The Training Loop
Loop through the dataset for a set number of epochs. In each epoch, set the model to training mode, loop through batches, compute the loss, and perform backpropagation:

```python
for epoch in range(NUM_EPOCHS):
    model.train()  # Set model to training mode
    
    for batch_idx, (features, targets) in enumerate(train_loader):
        # 1. Move data to device
        features = features.to(device)
        targets = targets.to(device)
        
        # 2. Forward pass
        logits = model(features)
        loss = criterion(logits, targets)
        
        # 3. Backward pass and optimization
        optimizer.zero_grad()  # Reset gradients from last step
        loss.backward()        # Compute gradients
        optimizer.step()       # Update weights
        
        # Optional: Logging
        if batch_idx % 100 == 0:
            print(f"Epoch: {epoch+1:02d}/{NUM_EPOCHS:02d} | "
                  f"Batch: {batch_idx:03d}/{len(train_loader):03d} | "
                  f"Loss: {loss.item():.4f}")
```

---

## Step 5: The Evaluation Loop
Evaluate model performance on the test set. Set the model to evaluation mode, disable gradient calculation to conserve memory, and compute accuracy:

```python
model.eval()  # Set model to evaluation mode
num_correct = 0
num_examples = 0

with torch.inference_mode():  # Disable gradient tracking (efficient inference)
    for features, targets in test_loader:
        features = features.to(device)
        targets = targets.to(device)
        
        # 1. Forward pass
        logits = model(features)
        
        # 2. Determine predictions
        _, predicted_labels = torch.max(logits, dim=1)
        
        # 3. Accumulate statistics
        num_examples += targets.size(0)
        num_correct += (predicted_labels == targets).sum().item()

accuracy = (num_correct / num_examples) * 100
print(f"Test Accuracy: {accuracy:.2f}%")
```

---
*From* → [[PyTorch Quick Reference]]
