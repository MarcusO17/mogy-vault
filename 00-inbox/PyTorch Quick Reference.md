Created : 2025-08-24 00:00
Tags :
Type :
Lecture : #L06
Video : https://www.youtube.com/watch?v=j1-r1vO2a_o

---
The PyTorch Boilerplate.

1.  Import Libraries
	- of course import torch
	- Other Useful ones,
		- ```
		   import torch
		   import torch.nn.functional as F
		   import torch.utils.data import DataLoader
		  ```
2.  Always initiate SETTINGS or globals
	- `device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")`
	- Hyperparameters
		- random_seed = 123
		- learning_rate 
		- num_epochs
		- batch_size
	- Architecture-related
		- num_features
		- num_classes
3. Initiate Model Class
	- `class Model(torch.nn.Module):`
	- Init function
		- must contain architecture attributes like e.g
			- num_features
			- num_classes
		- architecture must go next within the init function
		- ex. ``` def__init__(self,num_features,num_classes):
				  super(Model,self).__init__()
				  self.linear = torch.nn.Linear(num_features,num_classes)		
		- Remember to initialise weights! 
			- Usually this is auto with kaiming he, override if needed (usually this is the common practice (to override))
			- Use `nn.init.kaiming_normal_(self.layer)` (for ReLU) or `nn.init.xavier_uniform_(self.layer)` (for Sigmoid).
	- Forward Function
		- Explains how the forward pass works (Where the inputs goes through)
			- 1. data through model layers
				- activation in between
			- 2. then to a calssifier activation
			- 3. return logits and probas or depending on the classifier activation
		- 


