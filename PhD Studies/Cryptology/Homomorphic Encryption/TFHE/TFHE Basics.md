>[!note] Notation
>- $\left\lfloor r \right\rceil$ - nearest integer to $r$
>- $\mathbb{Z}_{q} = \mathbb{Z}\setminus q\mathbb{Z}$ - the set of integers reduced $\text{ mod } q$ centered around 0, i.e. $[  -\frac{q}{2}, \dots, \frac{q}{2}  ) \cap \mathbb{Z}$
>- $[\,\cdot\,]_{q}$ - reduction $\text{ mod } q$
>- $\mathbb{B} = \{ 0,1 \}$ - binary set
>- $[n] = \{ 1, \dots, n \}$ - integers up to $n$
>- $\mathbb{Z}^*_{q}$ - multiplicative subgroup of $\mathbb{Z}_{q}$
>- $a \leftarrow S$ - $a$ is sampled uniformly from $S$
>- $a \leftarrow \mathcal{D}$ - $a$ is sampled according distribution $\mathcal{D}$
>
>Given a polynomial $$P(X) = p_{0} + p_{1}X+\dots+ p_{N-1}X^{N-1} \in \mathbb{Z}_{q}[X]$$
>the $l_{1}, l_{2}$ and $l_{\infty}$ norms are defined as
>$$\begin{align}
>\lvert\lvert P \rvert\rvert_{1} &= \sum_{i=0}^{N-1} \lvert p_{i} \rvert  \tag{$l_{1}$-norm} \\
>\lvert\lvert P \rvert\rvert_{2} &= \sqrt{ \sum_{i=0}^{N-1} \lvert p_{i} \rvert^2  } \tag{$l_{2}$-norm} \\
>\lvert\lvert P \rvert\rvert_{\infty} &= \underset{0 \leq i \leq N-1}{\text{max}} \lvert p_{i} \rvert \; \tag{$l_{\infty}$-norm} 
>\end{align}$$

## Spaces

<u>Message Modulus:</u> $p$
<u>Ciphertext Modulus:</u> $q$

with $p \ll q$

Denote the $N$-th cyclotomic ring $$\mathcal{R}_{N}[X] = \mathbb{Z}[X]/(X^N + 1)$$ with $N$ being a power of $2$. Further we define
$$\mathcal{R}_{q,N} = \mathcal{R}_{N}/q\mathcal{R}_{N} = \mathbb{Z}_{q}[X]/(X^N + 1)$$

We have
- the message $M \in \mathcal{R}_{p,N}$
- the secret key $\boldsymbol{S}\in\mathcal{R}_{q,N}^k$
- the scaling factor $\Delta$