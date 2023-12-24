---
aliases:
- Generalized Linear Model
- Exponential Family
- Maximum Likelihood Generalization
---

>[!Source]-
>URL: https://www.jstor.org/stable/2344614
>PDF: [PDF](nelder1972.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@nelder1972)

>[!ABSTRACT]-
>The technique of iterative weighted linear regression can be used to obtain maximum likelihood estimates of the parameters with observations distributed according to some exponential family and systematic effects that can be made linear by a suitable transformation. A generalization of the analysis of variance is given for these models using log-likelihoods. These generalized linear models are illustrated by examples relating to four distributions; the Normal, Binomial (probit analysis, etc.), Poisson (contingency tables) and gamma (variance components). The implications of the approach in designing statistics courses are discussed.

### 1 - Model Definition
>[!def] Definition Family of Exponential Distributions
> $$ f(\mathbf{x}; \eta, \phi) = \exp\Big[\alpha({\phi}) \cdot \big(z\eta - g(\eta) + h(\mathbf{x}\big) + \beta(\phi, \mathbf{x})\Big]$$
> with $\alpha(\phi)>0$, $\phi$ fixed

| Parameter      | Meaning                                                                                                                     |
| -------------- | --------------------------------------------------------------------------------------------------------------------------- |
| $\mathbf{x}$   | random variable or observations                                                                                             |
| $\eta$         | natural parameters of the distribution                                                                                      |
| $\phi$         | nuisance parameter (see [[../Vocabulary\|Vocabulary]])  like $\sigma^2$ in normal distribution or $p$ in gamma distribution |
| $z$            | constant or function related to the sufficient statistic                                                                    |
| $\alpha(\phi)$ | helps to define the distribution over nuisance parameters                                                                                                                            |


### 2 - Fitting Procedure
