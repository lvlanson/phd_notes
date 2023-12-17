---
aliases:
- Bidirectional Multi-Label Classifier
---

>[!paper]
>p. 209
>![[../../../Literature/@nam2014|as]]

>[!def] Multi-Label Classification
>Let 
> - $\mathbf{X} = \set{\mathbf{x}_i}_{i=1}^t \subseteq \mathbb{R}^d$ the data points
> - $\mathbf{Y} = \set{0,1}^C$ the set of $C$-tuples
> - $\mathbf{X} \in \mathbb{R}^{t \times d}$
> - $\mathbf{Y} \in \mathbb{R}^{t \times C}$
> - $D = \set{(\mathbf{x}_i, y_i)}_{i=1}^t \subseteq \mathbb{R}^d \times \mathbf{Y}$ the labeled data set
> - $N$ the size of the data set
> - $C$ the amount of classes
> - $n$ the dimensionality of the data points
> - $y \in \set{0,1}^C$ be a **binary encoded** vector representing the classes associated to a data point $\mathbf{x} \in \mathbb{R}^d$
>> [!note]-
>> While one-hot encoded labels have only a single class association, a binary encoded label can have multiple, i.e. let $y_o$ be a one hot encoded label and $y_b$ a binary encoded label
>> $$∑i∈yoi=1∑i∈ybi≥0$$
> 
> A multi-label classification problem learns to associated multiple classes $c \in C$ to a data point $\mathbf{x} \in \mathbb{R}^d$

### Model Architecture
![[arch.png]]

### Encoding

>[!def] Encoding
> Let 
> - $\mathbf{S} \in \mathbb{R}^{t \times m},\mathbf{Z} \in \mathbb{R}^{t \times n}$ denote the latent representations of $\mathbf{X}$ and $\mathbf{Y}$ respectively.
>  - $\mathbf{W_{\mathbf{X}}} \in \mathbb{R}^{d \times m}, \mathbf{W_{\mathbf{Y}}} \in \mathbb{R}^{C \times n}$ denote the mappings for $\mathbf{X}$ and $\mathbf{Y}$ respectively.
> - $\mathbf{X} \in \mathbb{R}^{t \times d}, \mathbf{Y} \in \mathbb{R}^{t \times C}$ as defined earlier
> - $\sigma$ denote the sigmoid function $\sigma(\mathbf{x})=\frac{1}{1 + \exp(-\mathbf{x})}$
>
>The encoding is defined as
>$$\begin{align} \mathbf{S}&= \sigma\left(\mathbf{X}^T\mathbf{W}_{\mathbf{X}} + \mathbf{1}\mathbf{b}^T_{\mathbf{X}}\right) \
>\mathbf{Z}&= \sigma\left(\mathbf{Y}^T\mathbf{W}_{\mathbf{Y}} + \mathbf{1}\mathbf{b}^T_{\mathbf{Y}}\right)\end{align}$$
>with weights $\mathbf{b}_{\mathbf{X}} \in \mathbf{R}^n$ and  $\mathbf{b}_{\mathbf{Y}} \in \mathbf{R}^m$ 
>>[!note]-
>>A data point $\mathbf{x} \in \mathbb{R}^d$ will be embedded into smaller vector space. Hence, the linear mapping $\mathbb{S}: \mathbb{R}^d \rightarrow \mathbb{R}^m$ is an embedding into a lower dimensional vector space, i.e. $m < d$. Analogous for the labels $\mathbf{Y}$, i.e. $n < k$.

### Prediction
>[!def] Linear Regression Function
>$$Z^=f(X)=XΩ+1qT$$