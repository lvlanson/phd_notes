>[!def] Definition Continuity
>Let $f: \Omega \to \mathbb{R}$ be a function, then $f$ is **continuous** in $x_0$ if
>$$\forall \varepsilon>0: \exists\delta > 0: \forall x \in \Omega \text{ such that } \lvert\lvert x-x_{0} \rvert\rvert < \delta \implies \lvert\lvert f(x) - f(x_{0}) \rvert\rvert < \varepsilon  $$
>>[!note] $\delta$ depends on $\varepsilon$ and $x_{0}$
>
>>[!pic]-
>>![[Figures/continuity.png| center | 600]]

^dbc5ec

>[!def] Definition Uniform Continuity
>Let $f: \Omega \to \mathbb{R}$ be a function, then $f$ is **uniformly continuous** if
>$$\forall \varepsilon>0: \exists\delta > 0: \forall x,y \in \Omega \text{ such that } \lvert\lvert x-y \rvert\rvert < \delta \implies \lvert\lvert f(x) - f(x_{0}) \rvert\rvert < \varepsilon $$
>>[!note] $\delta$ only depends on $\varepsilon$
>
>>[!pic]-
>>![[Figures/uniform_continuity.png| center | 600]]

>[!def] Definition Lipschitz Continuity 
>Let $f: \Omega \to \mathbb{R}$ be a function, then $f$ is **Lipschitz continuous** if
>$$\exists K \in \mathbb{K}: \forall x,y \in \Omega: \lvert\lvert x-y \rvert\rvert \leq K\lvert\lvert f(x)-f(y) \rvert\rvert $$

^63aadd

>[!remark]
>Denote 
>$$\begin{align}
> C &- \text{ Set of Continuous Functions} \\
> UC &- \text{Set of Uniformly Continous Functions} \\
> LC &- \text{Set of Lipschitz Continuous Functions}
>\end{align}$$
>Then we can state the following relation
>$$LC \subset UC \subset C$$