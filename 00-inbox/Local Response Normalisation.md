---
tags:
  - "#normalisation"
---
[LocalResponseNorm — PyTorch 2.11 documentation](https://docs.pytorch.org/docs/stable/generated/torch.nn.LocalResponseNorm.html)

$$
 b_{c} = a_{c}\left(k + \frac{\alpha}{n}
        \sum_{c'=\max(0, c-n/2)}^{\min(N-1,c+n/2)}a_{c'}^2\right)^{-\beta}
$$

> [!PDF|yellow] [[NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper.pdf#page=4&selection=94,24,96,42&color=yellow|NIPS-20120-imagenet-classification-with-deep-convolutional-neural-networks-Paper, p.4]]
> > This sort of response normalization implements a form of lateral inhibition inspired by the type found in real neurons, creating competition for big activities amongst neuron outputs computed using different kernels. 


