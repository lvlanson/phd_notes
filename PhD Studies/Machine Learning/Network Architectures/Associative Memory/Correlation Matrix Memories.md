>[!source]
>Source 1: [[../../../../PDFs/kohonen1972.pdf|kohonen1972]]
>Source 2: [[../../../../PDFs/anderson1977.pdf|anderson1977]]

>[!def] Definition Correlation Matrix $\mathbf{A}$
>Let $\mathbf{f}_{i},\mathbf{g}_{i}\in\mathbb{R}^n$ denote two patterns and give the $i$-th association $(\mathbf{f}_{i}, \mathbf{g}_{i})$. Further, assume $\lvert\lvert f \rvert\rvert = 1.$ Then the correlation matrix over the two patterns can be given as
>$$\begin{align}
> \mathbf{A}_{1} &= \mathbf{f}_{1}\mathbf{g}_{1}^T \\
> \mathbf{A}_{i} &= \mathbf{A}_{i-1} + \mathbf{f}_{i}\mathbf{g}_{i}^T
>\end{align}$$

>[!def] Definition Information Retrieval
> Let $\mathbf{f}_{i} \in \mathbb{R}^n$ denote a pattern for which a stored memory $\mathbf{g}_{i}\in\mathbb{R}^n$ should be retrieved. Assume $\mathbf{f}_{i}$ are mutually orthogonal, i.e.
> $$\mathbf{f}_{i}^T\mathbf{f}_{j} = 0$$ 
>for all $i \neq j$, then 
>$$\mathbf{A}\mathbf{f}_{i} =\mathbf{g}_{i}$$
>>[!proof]-
>>$$\begin{align}
>>\mathbf{A}\mathbf{f}_{i}&=\mathbf{A}_{i}\mathbf{f}_{i} + \mathbf{A}_{j}\mathbf{f}_{i} \tag{$\mathbf{A}_i + \mathbf{A}_j = \mathbf{A}$}\\
>> &= \underbrace{ (\mathbf{f}_{i}\mathbf{g}_{i}^T) }_{ =\mathbf{A_{i}} }\mathbf{f}_{i} + \underbrace{ \left( \sum_{j \neq i} \mathbf{f}_{j}\mathbf{g}_{j}^T \right) }_{ =\mathbf{A}_{j} } \mathbf{f}_{i} \\
>> &= \mathbf{g}_{i}\underbrace{ (\mathbf{f}_{i}^T\mathbf{f}_{i}) }_{ = \lvert\lvert \mathbf{f}_{i} \rvert\rvert = 1  } + \sum_{j \neq i} \mathbf{g}_{j}\underbrace{ (\mathbf{f}_{j}^T\mathbf{f}_{i}) }_{ =0 } \\
>> &= \mathbf{g}_{i}
>>\end{align}$$

>[!remark] Remark on Information Retrieval
> Note, the vectors $\mathbf{f}_{i}$ are usually not orthogonal. This can be considered as noise when using such a model.
