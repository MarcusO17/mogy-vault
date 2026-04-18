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




## Architecture




