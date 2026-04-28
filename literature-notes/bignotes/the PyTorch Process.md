There is somewhat of a ML/PyTorch process.

# Starting
1.  Importing libraries 
	1. torch
2. Set Globals
	1. BATCH_SIZE, RANDOM_SEED, NUM_EPOCHS, DEVICE
	2. LEARNING_RATE


# Loading Data
1.  Load in datasets
	1. Use datasets library, pandas etc.
	2. Add in transforms as needed, transform.Compose()

2. Place in Data Loaders
	1. Train and Test loaders
	2. in batch


# Model
1. Class Model(torch.nn.Module)
	1. init func
		1. add in architecture
		2. weight init if needed.