---
aliases: 
- Binary Cross Entropy
- BCE Loss
- BCE with Logits Loss
- Multilabel Loss
- Probabilistic Classifier
---

>[!def]
>Let 
> - $l = (y_i)_{i=1}^C$ denote a **multi label** with $y_i \in \set{0,1}$ 
> - $\hat{l} = (\hat{y}_i)_{i=1}^C$ a **prediction** on a data point $\mathbf{x} \in \mathbb{R}^d$  with $\hat{y}_i \in [0,1]$
> - $C$ number of classes
>
>The **Binary Cross-Entropy** Loss is given as
>$$L_{BCE}(y, \hat{y}) = -\left(y \log(\hat{y}) + (1-y) \log(1-\hat{y})\right)$$


>[!example]
>```python
>from math import log
>
>def BCE(y, y_hat):
>	return -(y * log(y_hat) + (1-y) * log(1 - y_hat))
>
>l = [1, 0, 0, 1, 0]
>l_hat = [0.6, 0.2, 0.1, 0.8, 0.5]
>
>loss = [BCE(y, y_hat) for y, y_hat in zip(l, l_hat)]
>
>print(loss)
>```
