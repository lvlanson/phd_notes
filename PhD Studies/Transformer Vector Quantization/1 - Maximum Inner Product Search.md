---
aliases:
  - MIPS
---
All information can be found in [[../../Literature/@guo2015|@guo2015]]

>[!def] K-MIPS Problem
>The K - Maximum Inner Product Search (K-MIPS) finds the k prototypes with the highest inner product in the following search problem
>
>Let 
>* $X\subseteq \mathbb{R}^D$ denote a set of data points and
>* $\mathbf{q} \in \mathbb{R}^D$ denote a search query
>* $K > 0$ denote the amount of targets searched
>* $C = \{c_1, c_2, \ldots, c_K\}$ denote the set of candidate indices
>* $T = \{t_1, t_2, \ldots, t_K \}$ denote the set of target indices
>
 Finding the target set with $K$ targets can be found solving
 >
 > $$ T = \underset{\mathbf{x} \in X}{\text{arg max}^K} \{ \mathbf{x}^T\mathbf{q}\}$$
 > with $\mathbf{x} \in X$
   
 
>[!note]-
>The above <u>inner product</u> is the **Euclidean Inner Product**. An overview on inner products can be found here [[../Mathematic Basics/Inner Product/Inner Products|Inner Products]]
 
>[!remark]
> - **relevance** of an item $\mathbf{x}$ to a query $\mathbf{q}$ is represented by the dot-product
> - if targets are not calculated but instead **approximated**, these are called **candidates**
> - if $K=1$ it the algorithm is the vanilla Maximum Inner Product Search (MIPS)
> - **inference time** might be very high **if**
> 	- amount of data points is high => many dot products
> 	- dimension $d$, i.e. ($\mathbf{x,q} \in \mathbb{R}^d$), is high => many summands in dot-product, i.e. $\mathbf{x}^T\mathbf{q} = \sum_{i=1}^d x_i \cdot q_i$ 
> 	- ==> **Brute Force**: $\mathcal{O}(n \cdot d)$

>[!remark]
> * extreme multiclass or multilabel classification problems
> * language modeling with big vocabularies
> * information retrieval tasks (recommendation systems)
>
> ==> number of classes: $n >> 100$ 

