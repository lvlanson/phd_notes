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
>>This probability shifting is a _hard thresholding_ method

>[!def] Definition ASL
> ASL is an extension by setting $\gamma^+, \gamma^- \geq0$ with 
>$$ L_{F}(y, \hat{y}_m) = -\left(y (1-\hat{y}_m)^{\gamma^+} \log(\hat{y}_m) + (1-y) \hat{y}_m^{\gamma^-}\log(1-\hat{y}_m)\right)$$
>with $\gamma^- > \gamma^+$ because the contribution of positive examples should be focussed.
>>[!note]
>>In multilabel classification $y_i=0$ is not a class of itself as in binary classification. Here it means, it is not the class, hence, it's a _»negative example«_.