Created : 2025-08-19 14:47
Tags : #Model #NeuralNetwork #Classifier #LinearRegression 
Type : Model
Lecture : #L05
Video : 

---
# ADALINE

A physical device built by Widrow and Hoff in the 1960s.

![[Pasted image 20250819144823.png]]

ADALINE is a classifier. [[00-inbox/Linear Regression|Linear Regression]] and Adaline are very similar. The difference is that a threshold function for converting continuous outputs for predictions. 

The derivative and [[Online, Batch, and Minibatch Mode|training procedure]] are identical to ADALINE.  

---
## ADALINE Code using PyTorch.

- For ADALINE under the hood, refer to https://github.com/rasbt/stat453-deep-learning-ss21/blob/main/L06/code/adaline-with-autograd.ipynb.

This implementation will fully utilise PyTorch's API. For gradient computation theory, see[[Understanding Gradient Descent]]].

```python
import torch
import torch.nn.functional as F
```

```python
class Adaline(torch.nn.Module):
	def __init__(self, num_features):
		super(Adaline,self).__init__()
		self.linear = torch.nn.Linear(num_features,1) 
		
		self.linear.weight.detach().zero_()
		self.linear.bias.detach().zero_()
	
	def forward(self,x):
		netinputs = self.linear(x)
		activations = netinputs
		return activations.view(-1)
		
	
	def train(model, x, y, num_epochs, learning_rate=0.01, seed=123, minibatch_size=10):
		cost=[]
		
		torch.manual_seed(seed)
		
		optimizer = torch.optim.SGD(model.parameters(),lr=learning_rate)
		
		for e in range(num_epochs):
			
			shuffle_idx = torch.randperm(y.size(0), dtype=torch.long)
			minibatches = torch.split(shuffle_idx, minibatch_size)
			
			for minibatch_idx in minibatches:
			
				yhat = model.forward(x[minibatch_idx])
				
				loss = F.mse_loss(yhat, y[minibatch_idx])
				
				optimizer.zero_grad()
				
				loss.backward()
				
				optimizer.step() 
					
			 
			with torch.no_grad():
				yhat = model.forward(x)
				curr_loss = loss_func(yhat,y)   
				cost.append(curr_loss)
				
		return cost
		
```










---
# References


