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

> [!PDF|] [[1409.1556v6.pdf#page=2&selection=22,0,25,11|1409.1556v6, p.2]]
> > 2.1 ARCHITECTURE

Primary approach
> [!PDF|] [[1409.1556v6.pdf#page=2&selection=158,31,170,2|1409.1556v6, p.2]]
> > we use very small 3 × 3 receptive fields throughout the whole net, which are convolved with the input at every pixel (with stride 1).

1. Wh


### Takeaways

1.  LRN is useless on ILSRVC
> [!PDF|] [[1409.1556v6.pdf#page=2&selection=94,46,96,30|1409.1556v6, p.2]]
> >  as will be shown in Sect. 4, such normalisation does not improve the performance on the ILSVRC dataset, but leads to increased memory consumption and computation time.

