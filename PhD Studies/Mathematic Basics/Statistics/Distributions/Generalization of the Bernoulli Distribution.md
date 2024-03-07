---
aliases:
- Generalized Bernoulli Distribution
---

>[!source]
>Page 74
>PDF: [PDF](../../../../PDFs/bishop2006.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@bishop2006)

>[!Introduction]
>Random Variable can take $K$ different and mutually exclusive states, hence **multinomial variable**. For some state $X = x_i$ we use vector notation
>$$ \mathbf{x} = (0, \ldots , \underbrace{1}_{i\text{-th position}}, \ldots, 0)$$
>with $\sum_{i=1}^K x_i=1$

>[!def]
>The probability mass function $f: \mathbb{R} \rightarrow [0,1]$ is given as
>$$\begin{align} f(\mathbf{x};\mathbf{p}) &= \prod_{i=1}^K p_i^{x_i}\end{align}$$
>with

| Variable     | Meaning                                                                                                                |
| ------------ | ---------------------------------------------------------------------------------------------------------------------- |
| $\mathbf{x}$ | random variable states                                                                                                 | 
| $\mathbf{p}$ | probabilities corresponding to random variable states $f(x_i) = p_i$ <br> with $p_i \geq 0$ and $\sum_{i=1}^K p_i = 1$ |
