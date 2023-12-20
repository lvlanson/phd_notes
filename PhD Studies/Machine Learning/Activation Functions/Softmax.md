---
aliases:
- softmax
- normalized exponential
---

>[!Source]
>Page 114
>PDF: [PDF](bishop2006.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@bishop2006)

>[!Introduction]
>The softmax activation function is an extension of the [[Logistic Sigmoid]] activation function

>[!notation]
| Variable                                                 | Meaning                                                                                                                                           |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| $\mathbf{x} \in \set{0,1}^K$                             | multinomial random variable with $X=x_i$ is represented by  <br> $$ \mathbf{x} = (0, \ldots , \underbrace{1}_{i\text{-th position}}, \ldots, 0)$$ |
| $f(\mathbf{x})$                                          | probability distribution for random variable $\mathbf{x}$                                                                                         |
| $f_M(\mathbf{x;p})$                                      | Multinomial Bernoulli distribution with $f(\mathbf{x_i})=p_i$                                                                                     |
| $\set{\mathbf{x}_1, \mathbf{x}_2, \ldots, \mathbf{x}_N}$ | finite set of observations                                                                                                                        |
| $\mathbf{p} \in [0,1]^K$                                 | natural parameter representing the probabilityies for $\mathbf{x}$ with $\sum_{i=1}^K p_i = 1$                                                    |
| $K$                                                      | Amount of outcomes for the random variable $X$                                                                                                                                                  |

>[!def] Definition Generalized Bernoulli Distribution
> See [[../../Mathematic Basics/Statistics/Generalization of the Bernoulli Distribution|Generalized Bernoulli Distribution]]
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
| $h(\mathbf{x})$    | $=1$           | 
| $g(\mathbf{\eta}$ | $=1$           |
 