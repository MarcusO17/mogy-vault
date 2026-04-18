---
title: ImageNet Classification with Deep Convolutional Neural Networks
authors: Alex Krizhevsky, Ilya Sutskever, Geoffrey E. Hinton
publication date:
pdf:
url:
tags:
---
# Paper Excerpts

## Dataset

## Data Processing

> [!PDF|yellow] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=2&selection=46,10,65,70&color=yellow|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.2]]
> >  we down-sampled the images to a fixed resolution of 256 × 256. Given a rectangular image, we first rescaled the image such that the shorter side was of length 256, and then cropped out the central 256×256 patch from the resulting image. We did not pre-process the images in any other way, except for subtracting the mean activity over the training set from each pixel. So we trained our network on the (centered) raw RGB values of the pixels.
> 

1. Crop by Long Side, Resize to 256x256 and Normalize

## Key Points


###  ReLU Usage
> [!PDF|yellow] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=3&selection=119,21,123,11&color=yellow|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.3]]
> > However, on this dataset the primary concern is preventing overfitting, so the effect they are observing is different from the accelerated ability to fit the training set which we report when using ReLUs. 
> 
> 
	1. We are focused on it's training acceleration property rather than the prevention of overfitting.

### Local Response Normalisation
> [!PDF|yellow] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=4&selection=6,23,7,14&color=yellow|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.4]]
> > However, we still find that the following local normalization scheme aids generalization
> 
> 1. [[Local Response Normalisation]]
> 2. > [!PDF|yellow] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=4&selection=105,0,127,2&color=yellow|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.4]]
> >  k = 2, n = 5, α = 10−4, and β = 0.75
> 3. > [!PDF|yellow] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=4&selection=128,3,129,82&color=yellow|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.4]]
> > We applied this normalization after applying the ReLU nonlinearity in certain layers 
> 
> 
> 

> [!PDF|yellow] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=4&selection=130,0,132,14|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.4]]
> > This scheme bears some resemblance to the local contrast normalization scheme of Jarrett et al. [11], but ours would be more correctly termed “brightness normalization”, since we do not subtract the mean activity.
> 
> 


### Overlapping Pooling
> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=4&selection=166,8,191,32|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.4]]
> >  If we set s < z, we obtain overlapping pooling. This is what we use throughout our network, with s = 2 and z = 3. This scheme reduces the top-1 and top-5 error rates by 0.4% and 0.3%, respectively, as compared with the non-overlapping scheme s = 2, z = 2, which produces output of equivalent dimensions.
> >  
> >  > [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=4&selection=191,33,192,48|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.4]]
> > We generally observe during training that models with overlapping pooling find it slightly more difficult to overfit.
> 
> 

### Data Augmentation


> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=5&selection=84,7,98,58|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.5]]
> > We do this by extracting random 224 × 224 patches (and their horizontal reflections) from the 256×256 images and training our network on these extracted patches
> 
> > [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=5&selection=102,11,103,38|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.5]]
> > Without this scheme, our network suffers from substantial overfitting, which would have forced us to use much smaller networks


> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=5&selection=103,40,114,25|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.5]]
> > At test time, the network makes a prediction by extracting five 224 × 224 patches (the four corner patches and the center patch) as well as their horizontal reflections (hence ten patches in all), and averaging the predictions made by the network’s softmax layer on the ten patches.
> 
> 

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=0,0,1,52|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> 
> >To each training image, we add multiples of the found principal components, with magnitudes proportional to the corresponding eigenvalues times a random variable drawn from a Gaussian with mean zero and standard deviation 0.1
> 
> > [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=1,54,79,38|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > Therefore to each RGB image pixel Ixy = [IR xy , IG xy , IB xy ]T we add the following quantity: [p1, p2, p3][α1λ1, α2λ2, α3λ3]T where pi and λi are ith eigenvector and eigenvalue of the 3 × 3 covariance matrix of RGB pixel values, respectively, and αi is the aforementioned random variable.

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=86,22,87,100|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > This scheme approximately captures an important property of natural images, namely, that object identity is invariant to changes in the intensity and color of the illumination.
> 
> 

### Dropout

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=103,43,106,13|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > This technique reduces complex co-adaptations of neurons, since a neuron cannot rely on the presence of particular other neurons. It is, therefore, forced to learn more robust features that are useful in conjunction with many different random subsets of the other neurons

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=106,13,108,40|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > . At test time, we use all the neurons but multiply their outputs by 0.5, which is a reasonable approximation to taking the geometric mean of the predictive distributions produced by the exponentially-many dropout networks.
> 
> 


## Architecture




## Training Details

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=140,0,142,22|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > We trained our models using stochastic gradient descent with a batch size of 128 examples, momentum of 0.9, and weight decay of 0.0005

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=145,39,145,54|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > The update rule


> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=264,0,265,13|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > We initialized the weights in each layer from a zero-mean Gaussian distribution with standard deviation 0.01.

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=265,14,266,68|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > We initialized the neuron biases in the second, fourth, and fifth convolutional layers, as well as in the fully-connected hidden layers, with the constant 1
> 
> > [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=266,70,267,73|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > This initialization accelerates the early stages of learning by providing the ReLUs with positive inputs.
> 
> 

> [!PDF|] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=6&selection=267,74,268,51|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.6]]
> > We initialized the neuron biases in the remaining layers with the constant 0.
> 
> 
