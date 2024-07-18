Quelle: https://arxiv.org/pdf/2106.04554

## Introduction
>[!observation] Motivation
> Recall attention is a quadratic operation. 
>>[!recall]- Recall Attention
>>For some keys $\mathbf{K} \in \mathbb{R}^{M \times D_{k}}$ and queries $\mathbf{Q} \in \mathbb{R}^{N \times D_{k}}$ the attention matrix $\mathbf{A}$ is computed as
>> $$\mathbf{A} = \text{softmax}\left( \frac{\mathbf{Q}\mathbf{K}^T}{\sqrt{ D_{k} }} \right)$$
>> Finally, the attention matrix is evaluated by values $\mathbf{V} \in \mathbb{R}^{M \times D_{k}}$, such that
>> $$\text{Attention}(\mathbf{Q}, \mathbf{K}, \mathbf{V})= \mathbf{A}\mathbf{V}$$
>> where $D_{k}, D_{v}$ denotes respectively the number of key and query vectors $\mathbf{k}_{i}, \mathbf{q}_{i}$, and the number of value vector $\mathbf{v}_{i}$ 
> 
> The attention matrix $\mathbf{A}$ is often sparse, i.e. many $a_{ij}=0$, therefore we can **<u>reduce computations</u>**, since they are not contributing that much to the learning task.
> 

^2d06b4

## Position-Based Sparse Attention
>[!observation] Motivation 
> The attention matrix is limited in its computations by some predefined pattern.

>[!algo] Global Sparse Attention
> A set of global nodes $\{ \mathbf{k}_{i} \}_{i=1}^n$ and $\mathbf{q_{i}}_{i=1}^m$ is defined which attend to all other input nodes 
> 
> ![[Figures/attention_sparse_global.png|center|150]]

>[!algo] Band Sparse Attention
> Also known as *sliding window attention, local attention*. It captures mostly local interdependencies by restricting attention to the closest neighboring nodes.
> 
> ![[Figures/attention_sparse_band.png|center|150]]

>[!algo] Dilated Sparse Attention
>This is basically *band attention* with dilations in the band. Gaps of dilation with $w_{d}\geq 1$ are defined.
>
>![[Figures/attention_sparse_dilated.png|center|150]]

>[!algo] Random Sparse Attention
>Non-locality is increased by attending for randomly chosen queries $\mathbf{q}_{i}$ to randomly chosen keys $\mathbf{k}_{j}$
>
>![[Figures/attention_sparse_random.png|center|150]]

>[!algo] Block Local Attention
> Queries and keys are divided into **non-overlapping blocks**, such that attending keys to queries will only be performed inside the predefined blocks.
> 
> ![[Figures/attention_sparse_block_local.png|center|150]]

^62e8a4
