---
tags:
  - "#normalisation"
---
[LocalResponseNorm — PyTorch 2.11 documentation](https://docs.pytorch.org/docs/stable/generated/torch.nn.LocalResponseNorm.html)

$$
 b_{c} = a_{c}\left(k + \frac{\alpha}{n}
        \sum_{c'=\max(0, c-n/2)}^{\min(N-1,c+n/2)}a_{c'}^2\right)^{-\beta}
$$

