---
title: VERY DEEP CONVOLUTIONAL NETWORKS FOR LARGE-SCALE IMAGE RECOGNITION
authors: Karen Simonyan & Andrew Zisserman
publication date:
pdf: "[[1409.1556v6.pdf]]"
url:
tags:
---
# Paper Excerpts

> [!PDF|] [[1409.1556v6.pdf#page=1&selection=45,55,53,21|1409.1556v6, p.1]]
> > Our main contribution is a thorough evaluation of networks of increasing depth using an architecture with very small (3 × 3) convolution filters,

## Architecture


> [!PDF|] [[1409.1556v6.pdf#page=2&selection=27,0,35,9|1409.1556v6, p.2]]
> > During training, the input to our ConvNets is a fixed-size 224 × 224 RGB image
> 
> > [!PDF|] [[1409.1556v6.pdf#page=2&selection=35,11,36,98|1409.1556v6, p.2]]
> > The only preprocessing we do is subtracting the mean RGB value, computed on the training set, from each pixel.
> 
> 


> [!PDF|] [[1409.1556v6.pdf#page=2&selection=47,8,74,14|1409.1556v6, p.2]]
> >  In one of the configurations we also utilise 1 × 1 convolution filters, which can be seen as a linear transformation of the input channels (followed by non-linearity). The convolution stride is fixed to 1 pixel; the spatial padding of conv. layer input is such that the spatial resolution is preserved after convolution, i.e. the padding is 1 pixel for 3 × 3 conv. layers. 

> [!PDF|] [[1409.1556v6.pdf#page=2&selection=88,0,91,95|1409.1556v6, p.2]]
> > A stack of convolutional layers (which has a different depth in different architectures) is followed by three Fully-Connected (FC) layers: the first two have 4096 channels each, the third performs 1000way ILSVRC classification and thus contains 1000 channels (one for each class). The final layer is the soft-max layer. The configuration of the fully connected layers is the same in all networks.
> 
> > [!PDF|] [[1409.1556v6.pdf#page=2&selection=22,1,25,11|1409.1556v6, p.2]]
> > .1 ARCHITECTURE
> 
> 