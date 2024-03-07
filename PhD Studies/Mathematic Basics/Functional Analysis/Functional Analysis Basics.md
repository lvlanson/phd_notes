>[!def] Definition Cauchy Sequence ([[../../../PDFs/kreyszig1978.pdf#page=43|Source]])
>A sequence $(x_n)$ in a metric space $X=(X,d)$ is said to be **Cauchy** if for every $\varepsilon>0$ there exists some $N = N_{\varepsilon}$ such that
>$$d(x_{m}, x_{n})<\varepsilon$$
>for every $m,n>N$.

^dd46be

>[!def] Definition Space Completeness ([[../../../PDFs/kreyszig1978.pdf#page=43|Source]])
>A space $X$ is said to be **complete** if every Cauchy sequence in $X$ converges.

>[!property] Inequality Cauchy-Schwartz Inequality
> Let $\mathbf{x}, \mathbf{y} \in \mathbb{H}$ equipped with a scalar product $\langle \mathbf{x}, \mathbf{y}\rangle = \mathbf{x}^T\mathbf{y}$, then the Cauchy-Schwartz inequality can be given as
> $$\lvert \langle \mathbf{x}, \mathbf{y}\rangle \rvert = \lvert \mathbf{x}^T\mathbf{y} \rvert \leq \lvert\lvert \mathbf{x} \rvert\rvert \; \lvert\lvert \mathbf{y} \rvert\rvert    $$

^8d565e


>[!def] Definition $L_{p}$ Space ([[../../../PDFs/princeton_script.pdf|Source]])
> Let $1 \leq p < \infty$ and $X$ are measurable space with measure $\mu$ and the $\sigma$-algebra $\mathcal{F}$.  The $L_p$ space is given as the space of functions which satisfy for $f \in X$
> $$\int_{X} \lvert f(x) \rvert^p \,d\mu(x) < \infty$$
> 

>[!def] Definition $L_p$ Norm ([[../../../PDFs/princeton_script.pdf|Source]])
> The  $L_{p}$ norm is given as for $f \in X$
> $$\lvert\lvert f \rvert\rvert_{L_{p}(X,\mathcal{F}, \mu)} = \lvert\lvert f \rvert\rvert_{p} = \left( \int_{X} \lvert f(x) \rvert^p \,d\mu(x) \right)^{1/p}$$

^b3bce8
