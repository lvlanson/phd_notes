---
aliases: 
- Binary Cross Entropy
- cross entropy
- BCE Loss
- BCE with Logits Loss
- Multilabel Loss
- Probabilistic Classifier
- Balanced Cross Entropy
- Balanced Binary Cross Entropy
- balanced BCE
- balanced CE
---

>[!def] Definition Cross Entropy and Binary Cross Entropy
>Let 
> - $(y_i)_{i=1}^C$ denote a **multi label** with $y_i \in \set{0,1}$ 
> - or alternatively $y\in \set{0,1}$ for a **binary label**
> - $(\hat{y}_i)_{i=1}^C$ a **prediction** on a data point $\mathbf{x} \in \mathbb{R}^d$  with $\hat{y}_i \in [0,1]$
> - or alternatively $y \in [0,1]$ for a **binary classification**
> - $C$ number of classes
>
>The **Cross-Entropy** Loss for a _binary label_ is given as
>$$L_{CE}(y, \hat{y}) = -\left(y \log(\hat{y}) + (1-y) \log(1-\hat{y})\right)$$
>The **Binary Cross-Entropy** Loss for a _multi label_ is given as
>$$\begin{align}
>L_{BCE}(y_i, \hat{y_i}) &= -\sum_{i=1}^C\left(y_i \log(\hat{y_i}) + (1-y_i) \log(1-\hat{y_i})\right) \tag{Sum BCE}\\
>L_{BCE}(y_i, \hat{y_i}) &= -\frac{1}{C}\sum_{i=1}^C\left(y_i \log(\hat{y_i}) + (1-y_i) \log(1-\hat{y_i})\right) \tag{Mean BCE}
>\end{align}$$
>^defBCE

>[!note]
>The **cross-entropy** loss function for a binary classification can be obtained from the [[../../Mathematic Basics/Statistics/Methods/Maximum Likelihood Estimation|Maximum Likelihood Estimation]] on the [[../../Mathematic Basics/Statistics/Distributions/Bernoulli Distribution|Bernoulli Distribution]]. The **binary cross-entropy** computes the regular cross-entropy for each class and sums over each loss.

>[!example]
>```python
>from math import log
>
>def CE(y_i, y_i_hat, verbose=False):
>	if verbose:
>		print(f"Computing loss for {y_i=} and {y_i_hat=}")
>		print(f"y*log(y_i_hat)={y_i}*log({y_i_hat})=", y_i * log(y_i_hat))
>		print(f"(1-y_i) * log(1-y_i_hat)=(1-{y_i})*log(1-{y_i_hat})=",(1-y_i) * log(1 - y_i_hat), end="\n\n") 
>	return -(y_i * log(y_i_hat) + (1-y_i) * log(1 - y_i_hat))
>	
>def BCE(y, y_hat, type=None, verbose=False):
>	binary_losses = [CE(y_i, y_i_hat, verbose) for y_i,y_i_hat in zip(y, y_hat)]
>	if type == "mean":
>		return sum(binary_losses)/len(binary_losses)
>	elif type == "sum":
>		return sum(binary_losses)
>	else:
>		return  binary_losses
>		
>y = [1, 0, 0, 1, 0]
>y_hat = [0.6, 0.2, 0.1, 0.8, 0.5]
>
>print("BCE loss type sum", BCE(y, y_hat, type="sum", verbose=True))
>print("BCE loss type mean", BCE(y, y_hat, type="mean"))
>print("CE losses ", BCE(y, y_hat))
>```

>[!def] Definition Balanced (Binary) Cross Entropy
> Let $Y\subseteq\set{0,1}^{C  \times N}$ be an imbalanced dataset with
> - $C$ the  number of classes (for CE $C=2$, for BCE $C>2%
> - $N$ number of data points and labels
> - $Y$ set of labels
>
>and some classes $i,j \leq C$ being differently represented, i.e.$\sum_{k=1}^N y^{(k)}_i < \sum_{k=1}^N y^{(k)}_j$, with $y^{(k)}$ denoting the $k$-th label in $Y$.
>
>Let $\alpha \in [0,1]^C$ be a class weight, where lower $\alpha_i$ represent are relative higher representation.
>
>The **balanced Cross-Entropy** Loss is given as
>$$L_{CE}(y_i, \hat{y_i}) = -\alpha_i\left(y_i \log(\hat{y_i}) + (1-y_i) \log(1-\hat{y_i})\right)$$
>The **balanced Binary Cross-Entropy** Loss is given as
>$$\begin{align}
>L_{BCE}(y_i, \hat{y_i}) &= -\alpha_i\sum_{i=1}^C\left(y_i \log(\hat{y_i}) + (1-y_i) \log(1-\hat{y_i})\right) \tag{Sum BCE}\\
>L_{BCE}(y_i, \hat{y_i}) &= -\frac{\alpha_i}{C}\sum_{i=1}^C\left(y_i \log(\hat{y_i}) + (1-y_i) \log(1-\hat{y_i})\right) \tag{Mean BCE}
>\end{align}$$
>^defbalBCE

>[!def] Proposition
>The class weights $\alpha \in [0,1]^C$ can be calculated with
>$$ \alpha_i = \frac{N}{\sum_{j=1}^N y^{(j)}_i \cdot C}$$
>with
>- $N$ the number of samples
>- $\sum_{j=1}^N y^{(j)}_i$ the number class $i$ appears in the dataset
>- $C$ the number of classes

>[!example] Example Binary Classification
>```python
>import torch
>
>N = 100
>x = torch.rand(N)
>y = torch.round(torch.rand(N)**5) # powers of 5 ensures we have lots of zeros and rarely 1
>dataset = (x,y)
>
>def get_class_weights_binary(dataset):
>    x,y = dataset
>    
>    y_1_count = y.sum()
>    y_0_count = len(y) - y_1_count
>    
>    class_weights = [len(y)/(y_0_count*2), len(y)/(y_1_count*2)]
>    
>    return class_weights
>
>print(get_class_weights_binary(dataset))


>[!example] Example Multilabel Classification
>
>```python
>import torch
>
>N = 100
>C = 6
>x = torch.rand(N)
>y = torch.round(torch.rand(N, C)**3) # powers of 3 ensures we have lots of zeros and rarely 1
>dataset = (x,y)
>
>def get_class_weights(dataset):
>    x,y = dataset
>    C = len(y[0]) 
>    y_counts = y.sum(dim=0)
>    
>    class_weights = []
>    for y_count in y_counts:
>        class_weights.append(len(y)/(y_count*C))
>    return class_weights
>
>print(get_class_weights(dataset))
>```

>[!note]
>There are exist different weighting functions.