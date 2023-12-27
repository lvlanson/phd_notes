---
aliases:
- focal loss
- Focal Loss
- imballanced datasets
---
>[!sources]-
>URL: http://arxiv.org/abs/1708.02002
>PDF: [PDF](lin2018.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@lin2018)
>



>[!ABSTRACT]-
>The highest accuracy object detectors to date are based on a two-stage approach popularized by R-CNN, where a classifier is applied to a sparse set of candidate object locations. In contrast, one-stage detectors that are applied over a regular, dense sampling of possible object locations have the potential to be faster and simpler, but have trailed the accuracy of two-stage detectors thus far. In this paper, we investigate why this is the case. We discover that the extreme foreground-background class imbalance encountered during training of dense detectors is the central cause. We propose to address this class imbalance by reshaping the standard cross entropy loss such that it down-weights the loss assigned to well-classified examples. Our novel Focal Loss focuses training on a sparse set of hard examples and prevents the vast number of easy negatives from overwhelming the detector during training. To evaluate the effectiveness of our loss, we design and train a simple dense detector we call RetinaNet. Our results show that when trained with the focal loss, RetinaNet is able to match the speed of previous one-stage detectors while surpassing the accuracy of all existing state-of-the-art two-stage detectors. Code is at: https://github.com/facebookresearch/Detectron.

>[!note]
>The focal loss is based on the [[Binary Cross Entropy|cross entropy]] and [[Binary Cross Entropy]]. The underlying motivation for using the focal loss are **highly imbalanced datasets**. Though, in the paper the focal loss is used in a binary setting, i.e. on the cross entropy, it can be easily extended onto the binary cross entropy.
>

>[!observation]
>When having a highly imbalanced dataset, where one class is dominantly represented, learning with either cross entropy or binary cross entropy can lead to
>1. inefficient training, because 
>	- the highly represented class is too easy to guess
>	- the marginally represented class(es) don't contribute to learning
>2. easy data points (highly represented class) can lead to degenerate models due to training

>[!note] Suggested Solution
> Quote
>>[...] our focal loss is designed to address class imbalance by down-weighting inliers (easy examples) such that their contribution to the total loss is small even if their number is large. In other words, the focal loss performs the opposite role of a robust loss: it focuses training on a sparse set of hard examples.

>[!def] Definition Focal Loss
> Let 
> - $(y_i)_{i=1}^C$ denote a **multi label** with $y_i \in \set{0,1}$ 
> - or alternatively $y\in \set{0,1}$ for a **binary label**
> - $(\hat{y}_i)_{i=1}^C$ a **prediction** on a data point $\mathbf{x} \in \mathbb{R}^d$  with $\hat{y}_i \in [0,1]$
> - or alternatively $y \in [0,1]$ for a **binary classification**
> - $C$ number of classes
>
> The **binary focal loss** can be given as
> $$ L_{F}(y, \hat{y}) = -\left(y (1-\hat{y})^\gamma \log(\hat{y}) + (1-y) \hat{y}^\gamma\log(1-\hat{y})\right)$$
> The **multi label focal loss** can be given as
> $$\begin{align}
>L_{F}(y_i, \hat{y_i}) &= -\sum_{i=1}^C\left(y_i (1-\hat{y}_i)^\gamma\log(\hat{y_i}) + (1-y_i) \hat{y}^\gamma\log(1-\hat{y_i})\right) \tag{Sum Focal}\\
>L_{F}(y_i, \hat{y_i}) &= -\frac{1}{C}\sum_{i=1}^C\left(y_i (1-\hat{y}_i)^\gamma \log(\hat{y_i}) + (1-y_i) \hat{y}^\gamma \log(1-\hat{y_i})\right) \tag{Mean Focal}
>\end{align}$$
>with the **focus paramater** $\gamma \geq 0$

>[!note]-
>$\gamma = 0$  yields the CE/BCE loss function.

>[!note]-
>Lets deconstruct the loss of CE or BCE in $L = \begin{cases} L_{CE} \\ L_{BCE}\end{cases}$
>$$
>\begin{align}
>L = -\left(y\cdot L^+ + (1-y) \cdot L^-\right)
>\end{align}
>$$
>with
>$$\begin{cases} L^+ = \log(y_i)  \\ L^- = \log(1 - y_i) \end{cases}$$
>where 
>- $L^+$  denotes the loss regarding predicting that class $y_i = 1$ 
>- $L^-$  the loss for $y_i = 0$.
>
>>[!example]-
>>1 - <u> Easy, Correct Classification</u>
>>Assume belongs to class 1, i.e. $y=1$,  and we have the prediction $\hat{y}=0.8$, then
>>$$\begin{align} L^+ &= \log(0.8) \approx -0.09  \\ 
>>				L^- &= \log(0.2) \approx −0.7 \\ y \cdot 
>>				L^+ &= 1 \cdot (-0.09)= −0.09 \\ 
>>				(1-y) \cdot L^-&= 0 \cdot (−0.7) = 0 \end{align}$$ 
>> The loss therefore is
>>$$\begin{align} 
>>L &= -\left(y\cdot L^+ + (1-y) \cdot L^-\right) \\ 
>>  &=-(-0.09  + 0) \\ 
>>  &=  0.09\end{align}$$
>>2 - <u> Hard, Correct Classification</u>
>>Assume belongs to class 1, i.e. $y=1$,  and we have the prediction $\hat{y}=0.51$, then
>>$$\begin{align} L^+ &= \log(0.51) \approx −0.3  \\ 
>>				L^- &= \log(0.49) \approx -0.31 \\ 
>>				y \cdot L^+ &= 1 \cdot (-0.3) = −0.3 \\ 
>>				(1-y) \cdot L^-&= 0 \cdot (-0.31) = 0\end{align}$$ 
>> The loss is therefore is
>>$$\begin{align} 
>>L &= -\left(y\cdot L^+ + (1-y) \cdot L^-\right) \\ 
>>  &=-(-0.3  + 0) \\ 
>>  &=  0.3\end{align}$$
>>  <u>Conclusion</u>
>> As can be seen above, both correct classifications produce losses. Assuming class $y=1$ is highly overrepresented, our model would tend to produce more and more correct classifications for $y=1$. Since during training we would have many of these data points, where a set of these could be easy predictions, we would push the model further and further to predict the easy and correct predictions $y=1$. Since the other data points rarely appear, the model would not be able to correctly learn the other data points, while learning to predict easy data points.
> 
> Now we add the focal loss extension by adding the focal weights
> $$ L = -\left(y\cdot\underbrace{(1-\hat{y})^\gamma}_{L^+ \text{focus}} L^+ + (1-y)\cdot\underbrace{\hat{y}^\gamma}_{L^-\text{focus}} L^-\right) $$
> If the confidence of the prediction is high, then the factor of the $L^\pm$-focus is rather high too with maxing at $0.5^\gamma$.  As the confidence of the prediction converges to $1$, the focus weight converges to $0$.
> 
>>[!example]- Example Continued
>><u>Utilizing Focussing Parameter $\gamma$</u>
>>1:
>>For the easy, correct classification we have
>>$$\begin{align}
>>	\hat{y} &= 0.8 \\
>>	y &= 1 \\
>>	y \cdot L^+&=-0.09 \\
>>	(1-y) \cdot L^- &= 0
>>\end{align}$$
>>Further we calculate
>>$$\begin{align}
>>	(1-\hat{y}) &= 0.2
>>\end{align}$$
>>We set the focussing parameter $\gamma = 2$ as suggested in the paper, hence,
>>$$\begin{align}
>>L&=-\left(y\cdot\underbrace{(1-\hat{y})^\gamma}_{L^+ \text{focus}} L^+ + (1-y)\cdot\underbrace{\hat{y}^\gamma}_{L^-\text{focus}} L^-\right) \\
>> &= -\left(0.2^2\cdot (-0.09) + 0\right) \\
>> &= 0.04 \cdot0.09 \\
>> &= 0.0036
>>\end{align}$$
>>2:
>>For the hard, correct classification we have
>>$$\begin{align}
>>	\hat{y} &= 0.8 \\
>>	y &= 1 \\
>>	y \cdot L^+&=-0.3 \\
>>	(1-y) \cdot L^- &= 0
>>\end{align}$$
>>Again we calculate
>>$$\begin{align}
>>	(1-\hat{y}) &= 0.49
>>\end{align}$$
>>With $\gamma=2$ we have
>>$$\begin{align}
>>L&=-\left(y\cdot(1-\hat{y})^\gamma L^+ + (1-y)\cdot\hat{y}^\gamma L^-\right) \\
>> &= -\left(0.49^2\cdot (-0.3) + 0\right) \\
>> &= 0.072
>>\end{align}$$
>><u>Conclusion</u>
>>The focusing parameter of the focal loss allows us to non-linearly scale down easy classifications over the confidence of the prediction. The more uncertain a prediction is, the more this adaptation of the CE/BCE loss contributes to the gradient calculation. Easy predictions still contribute to the gradient, but are dramatically scaled down with the magnitude of its confidence.

>[!def] Definition Balanced Focal Loss
> Let $\alpha \in (0,1)$ denote the balancing parameter, then the _Balanced Focal Loss_ is given as
> $$ L =-\alpha\left(y\cdot(1-\hat{y})^\gamma L^+ + (1-y)\cdot\hat{y}^\gamma L^-\right)$$
> ^deffocallbalanced