There is somewhat of a ML/PyTorch process.

# Starting
1.  Importing libraries 
	1. torch
2. Set Globals
	1. BATCH_SIZE, RANDOM_SEED, NUM_EPOCHS, DEVICE
	2. LEARNING_RATE
	3. NUM_CLASSES/


# Loading Data
1.  Load in datasets
	1. Use datasets library, pandas etc.
	2. Add in transforms as needed, transform.Compose()

2. Place in Data Loaders
	1. Train and Test loaders
	2. Set Batch Size if needed

# Model
## Model Init
1. torch.manual_seed(RANDOM_SEED) #Fix
2. Class Model(torch.nn.Module)
	1. init func 
		1. add in architecture
		2. weight init if needed.
	2. forward
		1. forward pass, return logits (before output functions) / probas (after output function)
3. model init + model.to(DEVICE)
4. Loss and Optimizer (Loss can be done later)
	1. Can try NLL/MAE/MSE and SGD/Adam if unsure
## Model Training
1. Loop through Epoch
	1. model.train()
	2. Loop through Batches (enum loader)
		1. Send features and targets to DEVICE
		2.  forward pass
		3. compute COST/loss of pred to targets
		4. zero gradients of the optimizer
		5. backward pass 
		6. optim.step to update weights.

		7. OPTIONAL: Logging, print Epoch, Batch and cost count

### Evaluation
1. Evaluation
	1. Disable grad tracking (model.eval() and with torch.inference_mode())
	2. Loop through test loader
		1.  forward pass 
		2. argmax on probas 
		3. accumulate num_examples and pred_labels == targets. divide for acc.
			1. num_correct += (predicted == targets).sum().item() 
			2. num_examples += targets.size(0)
