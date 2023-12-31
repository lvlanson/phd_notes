---
aliases:
- ASL
- Asymmetric Focal Loss
- Asymetric Loss for Multi-Label Classfication
---

>[!Links]-
>URL: http://arxiv.org/abs/2009.14119
>PDF: [PDF](ben-baruch2021.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@ben-baruch2021)

>[!ABSTRACT]-
>In a typical multi-label setting, a picture contains on average few positive labels, and many negative ones. This positive-negative imbalance dominates the optimization process, and can lead to under-emphasizing gradients from positive labels during training, resulting in poor accuracy. In this paper, we introduce a novel asymmetric loss ("ASL"), which operates differently on positive and negative samples. The loss enables to dynamically down-weights and hard-thresholds easy negative samples, while also discarding possibly mislabeled samples. We demonstrate how ASL can balance the probabilities of different samples, and how this balancing is translated to better mAP scores. With ASL, we reach state-of-the-art results on multiple popular multi-label datasets: MS-COCO, Pascal-VOC, NUS-WIDE and Open Images. We also demonstrate ASL applicability for other tasks, such as single-label classification and object detection. ASL is effective, easy to implement, and does not increase the training time or complexity. Implementation is available at: https://github.com/Alibaba-MIIL/ASL.

>[!note]
>The asymmetric loss for multi-label classification (ASL) is based on the [[Focal Loss]], which again is based on [[Binary Cross Entropy|Cross Entropy]] and [[Binary Cross Entropy]].

>[!observation]
>When being in a multi-label classification setting, great imbalances in class distributions can occure quite frequently. While the focal loss was originally designed for binary classifications, challenges in multi-label classifications grow an additional burden on the loss function. The authors state
>>When using focal loss for multi-label training, there is an inner trade-off: setting high $\gamma$, to sufficiently down-weight the contribution from easy negatives, may eliminate the gradients from the rare positive samples.
>

>[!note] Suggested Solution
> Quote
>>[...]  We propose to decouple the focusing levels of the positive and negative samples. Let $\gamma^+$ and $\gamma^-$ be the positive and negative focusing parameters, respectively.

>[!def] Definition Asymmetric Probability Shifting
>Let $\hat{y}$ be some prediction with its label $y$. Then the probability shifted $\hat{y}_m$ by probability margin $m \in [0,1)$ is defined as
>$$ \hat{y}_m = \max(0, \hat{y}-m) $$
>>[!note]-
>>This probability shifting is a _hard thresholding_ method. It removes

>[!def] Definition ASL
> ASL is an extension of the focal loss by setting $\gamma^+, \gamma^- \geq0$ with 
>$$ L_{F}(y, \hat{y}_m) = -\left(y (1-\hat{y})^{\gamma^+} \log(\hat{y}) + (1-y) \hat{y}_m^{\gamma^-}\log(1-\hat{y}_m)\right)$$
>with $\gamma^- > \gamma^+$ because the contribution of positive examples should be focussed.
>>[!note]
>>In multilabel classification $y_i=0$ is not a class of itself as in binary classification. The meaning here is, it is not the class, hence, it's a _»negative example«_.

>[!example] Example Code
>Here we have 4 different predictions with different characteristics:
>- `y_hat_1` has **wrong** predictions with **low confidence overall**
>- `y_hat_2` has **wrong** predictions with **high confidence overall**
>- `y_hat_3` has only $1$ predictions with high confidence
>- `y_hat_4` has only $0$ predictions with high confidence
>
>Playing with the parameters yields the following effects:
>- The higher `m` is set, the more it removes negative residuals for negative predictions (`y=0`), i.e. <br> `y_hat = 0.2` with `m=0.2`, then `y_m = 0`. Therefore, it reduces the loss for correct negative predictions and increases the loss for incorrect positive predictions (`y=1`).
>- Increasing `gamma_minus` decreases the loss for negative predictions (`y=0`) with high confidence, and increases the loss with low confidence.
>- Increasing `gamma_plus` decreases the loss for negative predictions (`y=1`) with high confidence, and increases the loss with low confidence.
>
>```python 
>import torch
>from torch.nn.functional import threshold
>
>y = torch.tensor(         [0  ,  1   , 0  , 1  , 0  , 0  , 0  , 1], dtype=torch.float)
>y_hat_1 = torch.tensor([0.6, 0.4, 0.6, 0.4, 0.6, 0.6, 0.6, 0.4])
>y_hat_2 = torch.tensor([0.9 , 0.1 , 0.9, 0.1, 0.9, 0.9, 0.9, 0.1])
>y_hat_3 = torch.tensor([0.9 , 0.9 , 0.9, 0.9, 0.9, 0.9, 0.9, 0.9])
>y_hat_4 = torch.tensor([0.1 , 0.1 , 0.1, 0.1, 0.1, 0.1, 0.1, 0.1])
>
>
>class ASL:
>   
>    def __init__(self, gamma_plus, gamma_minus, m, reduction="sum", epsilon=1e-7):
>        self.gamma_plus = gamma_plus
>        self.gamma_minus = gamma_minus
>        self.m = m
>        self.epsilon = epsilon
>
>        if reduction not in ["sum", "mean"]:
>            raise Exception("mode must be 'sum' or 'mean'")
>        self.reduction = reduction
>
>    def __call__(self, y, y_hat):
>        y_m = threshold(y_hat-self.m, 0, self.epsilon) # probability shifting
>        y_hat = torch.clamp(y_hat, self.epsilon, 1) # making sure non of the values are zero for log-function
>        
>        L_plus = ((1-y_m)**self.gamma_plus) * y_m.log()
>        L_minus = (y_m**self.gamma_minus) * (1-y_m).log()
>        L = -1*(y*L_plus + (1-y)*L_minus)
>        L = L.nan_to_num()
>        if self.reduction == "sum":
>            L = L.sum()
>        elif self.reduction == "mean":
>            L = L.mean()
>        
>        return L
>        
>
>asl = ASL(gamma_plus=0, gamma_minus=4, m=0.2, reduction="mean")
>print(asl(y, y_hat_1))
>print(asl(y, y_hat_2))
>print(asl(y, y_hat_3))
>print(asl(y, y_hat_4))
>``` 