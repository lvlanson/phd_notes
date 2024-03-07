---
aliases:
- softmax
- normalized exponential
---

>[!Source]
>Page 114
>PDF: [PDF](../../../PDFs/bishop2006.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@bishop2006)

>[!Introduction]
>The softmax activation function is an extension of the [[Logistic Sigmoid]] activation function

>[!notation]
| Variable                                                 | Meaning                                                                                                                                           |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\mathbf{x} \in \set{0,1}^K$                             | multinomial random variable with $X=x_i$ is represented by  <br> $$ \mathbf{x} = (0, \ldots , \underbrace{1}_{i\text{-th position}}, \ldots, 0)$$ |
| $f(\mathbf{x})$                                          | probability distribution for random variable $\mathbf{x}$                                                                                         |
| $f_M(\mathbf{x;p})$                                      | multinomial Bernoulli distribution with $f(\mathbf{x_i})=p_i$                                                                                     |
| $\set{\mathbf{x}_1, \mathbf{x}_2, \ldots, \mathbf{x}_N}$ | finite set of observations                                                                                                                        |
| $\mathbf{p} \in [0,1]^K$                                 | natural parameter representing the probabilityies for $\mathbf{x}$ with $\sum_{i=1}^K p_i = 1$                                                    |
| $K$                                                      | Amount of outcomes for the random variable $X$                                                                                                                                                  |

>[!def] Definition Generalized Bernoulli Distribution
> See [[../../Mathematic Basics/Statistics/Distributions/Generalization of the Bernoulli Distribution|Generalized Bernoulli Distribution]]
>$$\begin{align} f(\mathbf{x};\mathbf{p}) &= \prod_{i=1}^K p_i^{x_i}\end{align}$$

>[!def] Definition Exponential Family of Distributions
>The exponential family of distributions over $\mathbf{x}$ given parameters $\eta$ is given as
>$$f(\mathbf{x}; \eta) = h(\mathbf{x})g(\mathbf{\eta}) \exp\left[\mathbf{\eta}^T \mathbf{u}(\mathbf{x})\right]$$
>with
>
| Parameter                | Meaning                                                                                                                                                                               |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\mathbf{\eta}$          | natural parameters of the probability distribution like in $f_B(\mathbf{x}) = p$ <br>the parameter $p$ is a natural parameter of the Bernoulli distribution, i.e. $f_B(\mathbf{x};p)$ |
| $g(\mathbf{\eta})$       | normalization parameter, i.e. $g(\mathbf{\eta})\int h(\mathbf{x}) \exp\left[\mathbf{\eta}^T \mathbf{u}(\mathbf{x})\right] \text{d}\mathbf{x}=1$                                       |
| $h(\mathbf{x})$          | function of observations $\mathbf{x}$                                                                                                                                                 |
| $\mathbf{u}(\mathbf{x})$ | statistics of the distribution                                                                                                                                                                                      |

>[!Derivation]
>$$\begin{align}
>f(\mathbf{x}; \mathbf{p}) &= \prod_{i=1}^K p_i^{x_i} \\
>						  &= \prod_{i=1}^K \exp \Big[\text{ln } p_i^{x_i}\Big] \\
>						  &= \prod_{i=1}^K \exp \Big[x_i \text{ln } p_i\Big] \\
>						  &= \exp \Big[\sum_{i=1}^K x_i \text{ln } p_i\Big]
>\end{align}$$
>We identify $\mathbf{\eta} = (\eta_1, \ldots, \eta_K)$ with $\eta_i = \text{ln } p_i$ and formulate
>$$ \begin{align} f(\mathbf{x}, \mathbf{\eta}) = \exp\left[\mathbf{\eta}^T \mathbf{x}\right]\end{align}$$
>with 
>
| Parameter         | Identification |
| ----------------- | -------------- |
| $u(\mathbf{x})$   | $= \mathbf{x}$ |
| $h(\mathbf{x})$   | $=1$           |
| $g(\mathbf{\eta}$ | $=1$           |
 >
 >Recall $p_i \in [0,1]$ with $\sum_{i=1}^K p_i = 1$ and $x_i \in {0,1}^K$ with $\sum_{i=1}^{K} x_i = 1$, therefore we can fix $p_K$ and $x_K$ as
 >$$ \begin{align}p_K = 1 - \sum_{i=1}^{K-1} p_i \\
 >	x_K = 1-\sum_{i=1}^{K-1} x_i\end{align}$$
 >with $0\leq p_i \leq 1$ and $\sum_{i=1}^{K-1}p_k \leq 1$.
 >
 >We now derive the formula for a specific $\eta_k$ from the representation of the family of exponential distributions we described earlier 
 >$$\begin{align}\exp\left[\sum_{i=1}^K x_i \text{ ln } (p_i)\right] &= \exp\left[\sum_{i=1}^{K-1} x_i \text{ ln } (p_i) + x_K \text{ ln } (p_K)\right] \\
 >&= \exp\left[\sum_{i=1}^{K-1} x_i \text{ ln } (p_i) + \left(1 - \sum_{i=1}^{K-1} x_i \right) \text{ ln } \left(1 - \sum_{i=1}^{K-1}p_i\right)\right] \\
 >&= \exp\left[\sum_{i=1}^{K-1}  x_i \text{ ln } (p_i) - \cancel{\sum_{i=1}^{K-1}}x_i \text{ ln }\left(1-\sum_{j=1}^{K-1} p_j \right) + \text{ ln } \left(1 - \sum_{i=1}^{K-1}p_i\right)\right] \\
 >&= \exp\left[\sum_{i=1}^{K-1}  x_i \left(\text{ ln } (p_i) -  \text{ ln }\left(1-\sum_{j=1}^{K-1} p_j \right)\right) + \text{ ln } \left(1 - \sum_{i=1}^{K-1}p_i\right)\right] \\
 >&= \exp\left[\sum_{i=1}^{K-1}  x_i \underbrace{\text{ ln } \left(\frac{p_i}{\text{ ln }\left(1-\sum_{j=1}^{K-1} p_j \right)} -  \right)}_{= \eta_k} + \text{ ln } \left(1 - \sum_{i=1}^{K-1}p_i\right)\right] 
 >\end{align}$$
 >Having found an expression for a specific $\eta_k$ we can now solve for the corresponding specific $p_k$

 