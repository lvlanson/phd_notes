# Probability Review
#### Quick Facts
- $(\Omega, \mathcal{A}, \mathbb{P})$ - Probability Space
	- $\Omega$ - Sample Space
	- $\mathcal{A}$ - Sigma Field
	- $\mathbb{P}$ - Probability Measure
- $X: \Omega \to \mathbb{R}$ - Random Variable
	- with $X^{-1}\Big((-\infty, x]\Big) = \{ \omega \in \Omega: X(\omega)\leq x \} \in \mathcal{A}$ for all $x \in \mathbb{R}$
	- the set $X^{-1}\Big((-\infty, x]\Big)$ is said to be measurable
-

#### Cumulative Distribution and Probability Density Function

>[!def] Definition Cumulative Density Function (CDF)
> Let $X$ be a random variable. The function
> $$\begin{align}
> &F : \mathbb{R} \to [0,1] \\
> &F : F(x) \mapsto \mathbb{P}[X \leq x]
>\end{align}$$
>is called the **<span style="color:#38ffa9">cumulative density function</span>**. Given independent and identically distributed (iid) samples $X_{1},\dots,X_{n}$ are given, the CDF can estimated via the **<span style="color:#38ffa9">empirical distribution function</span>** (ecdf)
>$$F_{n}(x)= \frac{1}{n}\sum_{i=1}^n \mathbb{1}_{{X_{i \leq x}}}$$
>with 
>$$\mathbb{1}_{A}:=\begin{cases}
> 1, & A \text{ is true} \\
> 0, & A \text{ is false}
>\end{cases}$$
>being the indicator function.


