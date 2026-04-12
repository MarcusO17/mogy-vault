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

1. Utilise ReLU for It's non-linearity.


## Architecture




