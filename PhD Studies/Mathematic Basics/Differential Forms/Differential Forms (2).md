# 2.1 1-Forms

>[!def] Definition 1-Form
> Let $\mathcal{R}$ be a region in $\mathbb{R}^n$. A 1-form $\phi$ on $\mathcal{R}$ is a smooth linear function on the tangent spaces $T_p \mathbb{R}^n$ at each point $p$ of $\mathcal{R}$. That is
> 1. **LINEARITY** 
> For any fixed point $p \in \mathcal{R}$
> $$\phi : T_p \mathbb{R}^n \longrightarrow \mathbb{R}$$
> is a linear function, i.e. $\phi(c \boldsymbol{v}_{p} + d \boldsymbol{w}_{p}) = c \phi(\boldsymbol{v}_{p}) + d \phi(\boldsymbol{w}_{p})$
> 2. **SMOOTHNESS** 
> For any smooth vector field $\boldsymbol{F}$ on $\mathcal{R}$, the function $e: \mathcal{R} \longrightarrow \mathbb{R}$ given by $e(p) = \phi(\boldsymbol{F}(p))$ is a smooth function

^e1192a

>[!def] Definition 
> The 1-form $dx_i$ on $\mathbb{R}^n$ is defined as follows. For any point $p$ in $\mathbb{R}^n$, $dx_i$ is the linear function on $T_p \mathbb{R^n}$ given by: $$dx_i\left(\boldsymbol{e}^i_p\right) = 1 \text{ and } dx_i\left( \boldsymbol{e}^j_p\right) = 0 \text{ for } j \neq i$$

>[!remark] Remark on the Meaning
> Note that the vector field $\boldsymbol{F}$ takes as input points $p \in \mathcal{R} \subseteq \mathbb{R}^n$, i.e.
> $$\begin{align}\boldsymbol{F}&: \mathcal{R} \subseteq \mathbb{R}^n \longrightarrow \mathbb{R}^n \\
> \boldsymbol{F}(x) &= \sum_{i=1}^{n} \boldsymbol{F}^i(x)\frac{\partial}{\partial x_i} 
>\end{align}$$
> where  $\boldsymbol{F}^i(p)$ denotes the $i$-th component of the vector field at some point $p \in \mathcal{R}^n$ and $\frac{\partial}{\partial x_i}$ denotes the corresponding basis vector. In the previous chapter we defined a 1-form as
> $$\phi = \sum_{i=1}^{n} A_i \, dx_i$$
> Now note that by the more specific definition of this section the 1-form $\phi$ takes as input some vector of the tangent space $\mathbb{R}^n \cong T_p \mathbb{R}^n$ at point $p \in \mathcal{R} \subseteq \mathbb{R}$.
> $$\begin{align}
> \phi&: T_p \mathbb{R}^n \longrightarrow \mathbb{R} \\
>\end{align}$$
>
> The concatenation of $\phi$ and $\boldsymbol{F}$ gives
> $$\phi (\boldsymbol{F}): \mathcal{R} \longrightarrow T_p \mathbb{R}^n \longrightarrow \mathbb{R}$$
> Thus, evaluating a 1-form on a vector field boils down to 
> $$\begin{align}
> \phi(\boldsymbol{F})&= \sum_{i,j}\Big(A_i(x) \, dx_i \Big) \left(\boldsymbol{F}^j(x)\frac{\partial}{\partial x_j}\right) \\
> &= \sum_{i,j}A_i(x) \, \boldsymbol{F}^j(x)dx_i \left(\frac{\partial}{\partial x_j}\right) \\
>\end{align}$$
> where we have $$dx_i \left(\frac{\partial}{\partial x_j}\right) = \begin{cases} 1 & i = j \\ 0 & i \neq j \end{cases}$$
> Thus
> $$\phi(\boldsymbol{F}) = \sum_{i} A_i(x)\boldsymbol{F}^i(x)$$

>[!theorem]
> Let $\mathcal{R}$ be a region in $\mathbb{R}^n$. Let $A^1(x_1, \ldots, x_n), \ldots, A^n(x_1, \ldots, x_n)$ be smooth functions on $\mathcal{R}$. Then
> $$\phi = A^1 \, dx_1 + \ldots + A^n \, dx_n$$
> is a 1-form on $\mathcal{R}$. Conversely, every 1-form $\phi$ on $\mathcal{R}$ can be written in this way, for unique smooth functions $A^1, \ldots, A^n$ on $\mathcal{R}$.

>[!proof]-
> $\phi$ defines a function on tangent vector to point $p$ in $\mathcal{R}$ as
> $$\phi(\boldsymbol{v}_{p}) = A^1(p)\, dx_1(\boldsymbol{v}_{p}) + \ldots + A^n(p) \, dx_n(\boldsymbol{v}_{p})$$
> To show that $\phi$ is a 1-form, we must show that the definition holds, i.e.
> - **Linearity**:
> Since $\phi$ is a linear combination of differentials, which in themselves are linear, $\phi$ must be linear itself.
> - **Smoothness**: 
> Let $\boldsymbol{F}$ be the smooth vector field on $\mathcal{R}$ given by
> $$\boldsymbol{F} = f^1 \boldsymbol{e}^1 + \ldots + f^n \boldsymbol{e}^n$$
> i.e. by
> $$\boldsymbol{F}(p) = f^1(p) \boldsymbol{e}^1_p + \ldots + f^n(p) \boldsymbol{e}^n_p$$
> Then $dx_i(\boldsymbol{F}(p)) = f^i(p)$ and we get
> $$e(p) = \phi(\boldsymbol{F}(p)) = A^(p)f^1(p) + \ldots + A^n(p) f^n(p)$$
> Since $A^i$ and $f^i$ is smooth, their product is also smooth.
>
> For the converse claim, let $\phi$ be a 1-form on $\mathcal{R}$. For each $i$, we define a function $A^i$ by
> $$A^i(p) = \phi\left( \boldsymbol{e}^i_p \right)$$
> Note that $\boldsymbol{e}^i$ is a constant vector field, so it is smooth. By [[#^e1192a| this definition (2)]] each $A^i$ is smooth. Each $A^1,\ldots, A^n$ is uniquely defined by $\phi$. Let $$\psi = A^1 \, dx_1 + \ldots + A^n \, dx_n$$
> $\psi$ is a linear function for each $p$ of tangent spaces $T_p \mathbb{R}^n$. Furthermore, for any $i$,
> $$\begin{align}\psi\left( \boldsymbol{e}^i_p \right) &= \left(\sum_{i=1}^{n} A^i(p) \, dx_i \right)(\boldsymbol{e}^i_p) \\
> &= A^i(p) = \phi(\boldsymbol{e}^i_p)\end{align}$$
> Thus $\phi$ and $\psi$ are linear functions that agree on the basis $\{\boldsymbol{e}_{p}^1, \ldots, \boldsymbol{e}_{p}^n\}$ of $T_p \mathbb{R}^n$, so $\phi = \psi$ on $T_p \mathbb{R}^n$. Since this is true for every $p \in \mathcal{R}$, and therefore $\phi = \psi$, i.e. the 1-form is a composition of unique smooth functions. $$\tag*{$\square$}$$

>[!lemma] Corollary
> Lert $\mathcal{R}$ be a region in $\mathbb{R}^n$. Let
> $$\phi = A^1 \, dx_1 + \ldots + A^n \, dx_n$$
> be a 1-form on $\mathcal{R}$ and let 
> $$\boldsymbol{F}=f^1 \boldsymbol{e}^1 + \ldots + f^n \boldsymbol{e}^n$$
> be a vector field on $\mathcal{R}$.
> Then for any point $p \in \mathcal{R}$,
> $$\phi(\boldsymbol{F}(p)) = A^1(p)f^1(p) + \ldots + A^n(p)f^n(p)$$

>[!proof]-
> Result from the previous theorem.

>[!example]
> 1. Let $\mathcal{R} = \mathbb{R}^3$. Let $\phi$ be the constant 1-form $\phi = dx + 2 \, dy - 3 \, dz$ and let $\boldsymbol{v}$ be the constant vector field $\begin{bmatrix} 2 \\ 4 \\ 3 \end{bmatrix}$. Then at any point $p$ of $\mathcal{R}$
> $$\begin{align}
> \phi(\boldsymbol{v}_p) =\; & (dx_1 + 2dx_2 - dx_3)(2 \boldsymbol{e}_p + 4 \boldsymbol{e}_2 + 3 \boldsymbol{e}_3) \\
> = \;& 2\, dx_1(\boldsymbol{e}_1) + 4 \, dx_1 (\boldsymbol{e}_2) + 3 \, dx_1 (\boldsymbol{e}_3) \\
> &+ 4\, dx_2(\boldsymbol{e}_1) + 8 \, dx_2(\boldsymbol{e}_2) + 6 \, dx_2(\boldsymbol{e}_3) \\
> &+ -6\, dx_3(\boldsymbol{e}_1) - 12\, dx_3(\boldsymbol{e}_2) - 9 \, dx_3(\boldsymbol{e}_3) \\
> = \;& \, 2 \cdot 1 + 4 \cdot 0 + 3 \cdot 0 \\
> & + 4 \cdot 0 + 8 \cdot 1 +  6 \cdot 0 \\
> & -6 \cdot 0 - 12 \cdot 0 - 9 \cdot 1
>\end{align}$$
> 2. Let $\mathcal{R} = \mathbb{R}^2 - (0,0)$. Let $\boldsymbol{v}$ be the vector field given by $\boldsymbol{v}_{p} = \begin{bmatrix}-y \\ x \end{bmatrix}_{p}$ for any point $p \in \mathcal{R}$. Let $\phi^1$ be the 1-form 
> $$\phi^1 = \frac{-y}{(x^2 + y^2)}\, dx + \frac{x}{(x^2 + y^2)}\, dy$$
> Then
> $$\begin{align}
> \phi(\boldsymbol{v}_p) &= \left( \frac{-y}{x^2 + y^2} \, dx + \frac{x}{x^2+ y^2} \, dy\right)(-y \boldsymbol{e}_1 + x \boldsymbol{e}_2) \\
> &= \frac{y^2}{x^2 + y^2} \, dx(\boldsymbol{e}_1) + \frac{x^2}{x^2+y^2} \, dy(\boldsymbol{e}_2) \\
> &= \frac{x^2 + y^2}{x^2 + y^2} \\
> &= 1
>\end{align}$$
> Next let $\omega = \frac{x}{x^2+y^2}\, dx + \frac{y}{x^2+y^2}\, dy$, then
> $$\begin{align}\omega(\boldsymbol{v}_{p}) &= \left( \frac{x}{x^2+y^2} \, dx + \frac{y}{x^2+y^2} \, dy \right) (-y \boldsymbol{e}_{1} + x \boldsymbol{e}_{2}) \\ &= \frac{-xy}{x^2+y^2} \,dx(\boldsymbol{e}_{1}) + \frac{xy}{x^2+y^2}\,dy(\boldsymbol{e}_{2}) \\ &=\frac{xy -xy}{x^2+y^2} \\ &= 0\end{align}$$

>[!theorem]
> Let $\mathcal{R}$ be a region in $\mathbb{R}^n$ and let $g$ be a smooth function on $\mathcal{R}$, i.e. $g: \mathcal{R} \subseteq \mathbb{R}^n \longrightarrow \mathbb{R}$. Let $p$ be any point of $\mathcal{R}$ and let $\boldsymbol{v}_{p} \in T_p \mathbb{R}^n$ be any tangent vector at $p$. Let $$r:(- \delta, \delta) \longrightarrow \mathcal{R}$$ be any smooth function with 
> 1. $r(0) = p$
> 2. $r'(0) = \boldsymbol{v}_{p}$
>
> where $\delta$ is any positive real number. Define the function
> $$e:(-\delta, \delta) \longrightarrow \mathbb{R}$$ by $$e(t) = g(r(t))$$
> Then $$dg(\boldsymbol{v}_{p}) = e'(0)$$

>[!proof]-
> We want to show that $$dg(\boldsymbol{v}_{p}) = e'(0)$$
> given the definitions of the theorem. By simple computations using the chain rule we get
> $$\begin{align}
> e'(0) &= g'\Big(r(0) \Big) \, r'(0) \\
> &= g'(p) \, \boldsymbol{v}_p \tag{1 and 2}
>\end{align}$$
> Note that $g: \mathcal{R} \subseteq \mathbb{R}^n \longrightarrow \mathbb{R}$, thus the derivative is the Jacobian
> $$g'(p) = \Big[ g_{x_1}(p) \, \ldots \, g_{x_n}(p) \Big]$$
> This is the dot product for $\boldsymbol{v}_{p} = \begin{bmatrix} a_1 \\ \vdots \\ a_n\end{bmatrix}_{p}$
> $$\begin{align}
> e'(0) &= \Big[ g_{x_1}(p) \, \ldots \, g_{x_n}(p) \Big] \begin{bmatrix} a_1 \\ \vdots \\ a_n\end{bmatrix}_p \\
> &= g_{x_1}(p) a_1 + ... g_{x_n}(p) a_n
> \end{align}$$
> Note that $$g_{x_i}(p)a_i = g_{x_i}a_i\, dx_i(\boldsymbol{e}_{i}) = \Big( g_{x_i} \, dx_i \Big) ( a_i \boldsymbol{e}_{i})$$
> Thus
> $$\begin{align}
> e'(0) &=\Big(g_{x_1}(p)\, dx_1 + ... + g_{x_n}(p) \, dx_n \Big) (\boldsymbol{v}_p) \\
> &= d\big(g(p)\big)(\boldsymbol{v}_p) \tag*{$\square$}
>\end{align}$$

>[!remark]
> In this theorem we have a few fixed entities
> - a region $\mathcal{R} \subseteq \mathbb{R}^n$
> - a smooth function $g: \mathcal{R} \subseteq \mathbb{R}^n \longrightarrow \mathbb{R}$
> - a point $p \in \mathcal{R}$
> - a tangent vector $\boldsymbol{v}_{p} \in T_p \mathbb{R}^n$
>
> We are given to choose some smooth function/curve $$r:(-\delta, \delta) \longrightarrow \mathcal{R}$$ $$\begin{align}
> r(0) &= p \\
> r'(0) &= \boldsymbol{v}_p
>\end{align}$$
> The purpose of $r$ is to reduce the multivariable situation of $g$ to a single variable, such that we can define a single-variable function $e$ such that
> $$e: (-\delta, \delta) \longrightarrow \mathbb{R}$$
> by definig $$e(t) = g(r(t))$$
> Thus
> $$\begin{align}
> e &: (-\delta, \delta) \longrightarrow \mathcal{R} \longrightarrow \mathbb{R} \\
> e(t) &= (g \circ r)(t) = g(r(t))
>\end{align}$$
> This enables us to take the derivative of $g$, which corresponds to the derivative of $e$. When looking into the proof, one notices that the derivative of $g$ is in fact the exterior derivative.

>[!def] Definition Directional Derivative
> Let $\mathcal{R}$ be a region in $\mathbb{R}^n$ and let $g$ be a smooth function on $\mathcal{R}$. Let $p$ be any point of $\mathcal{R}$ and let $\boldsymbol{v}_{p} \in T_p \mathbb{R}^n$ be any tangent vector to $\mathbb{R}^n$ at $p$. Let $\boldsymbol{v}$ be the constant vector field on $\mathcal{R}$ whose value at $p$ is $\boldsymbol{v}_{p}$. Then $D_{\boldsymbol{v}_{p}}(g)$, the **derivative of $g$ along the vector $\boldsymbol{v}_{p}$** is $$D_{\boldsymbol{v}_{p}} = \lim_{t \longrightarrow 0} \frac{g(p + t \boldsymbol{v}) - g(p)}{t}$$

>[!lemma] Corollary
> Let $\mathcal{R}$ be a region in $\mathbb{R}$ and let $g$ be a smooth function on $\mathcal{R}$. Let $p$ be any point of $\mathcal{R}$ and let $\boldsymbol{v}_{p} \in T_p \mathbb{R}^n$ be any tangent vector at $p$. Then
> $$dg(\boldsymbol{v}_{p}) = D_{\boldsymbol{v}_{p}}(g)$$

>[!proof]-
> By the previous theorem we choose a smooth function
> $$r(t) = p + t \boldsymbol{v}$$
> where $\boldsymbol{v}$ is the constant vector field which has value $\boldsymbol{v}_{p}$ at point $p$. The conditions $r(0) = p$and $r'(0) = \boldsymbol{v}_{p}$ hold. Hence we can find the derivative as
> $$dg(\boldsymbol{v}_{p}) = e'(0)$$
> with $e(t) = g(r(t))$. We get
> $$\begin{align}
> e'(0) &= \lim_{t \longrightarrow 0} \frac{e(t) - e(0)}{t} \\
> &= \lim_{t \longrightarrow 0} \frac{g(p+t \boldsymbol{v}) - g(p)}{t} \\
> &= D_{\boldsymbol{v}_p}(g) \tag*{$\square$}
>\end{align}$$

>[!remark] Remark on Cotangent Vectors
> A linear function on tangent vectors is often called **cotangent vector**. Thus a 1-form on $\mathcal{R}$ is a smooth cotangent vector field on $\mathcal{R}$.
>
> To summarize:
> - vector field $\boldsymbol{v}: \mathcal{R} \longrightarrow \mathbb{R}^n$ assigns to each point $p$ a **tangent vector** $\boldsymbol{v}_{p} \in T_p \mathbb{R}^n$ at point $p \in \mathbb{R}^n$
> - a 1-form $\phi_p$ gives a **cotangent vector** $\phi_p \in T_p^* \mathbb{R}^n$
>
> Note, that $T_p^*\mathbb{R}^n$ is the dual space of $T_p \mathbb{R}^n$ and consists of all linear functionals (1-forms) evaluating **tangent vectors** to $\mathbb{R}$.

## 2.2 $k$-forms

>[!def] Definition $k$-Form
> A $k$-form on a region $\mathcal{R}$ in $\mathbb{R}^n$ is a smooth multilinear alternating function on $k$-tuples of tangent vetor to $\mathbb{R}^n$, all of which are based at the same point $\mathcal{R}$.
>
> Thus, if $\phi$ is a $k$-form on $M$, and $\boldsymbol{v}_{p}^1, \ldots, \boldsymbol{v}_{p}^k$ are vectors all of which are tangent to $\mathbb{R}^n$ at some point $p \in \mathcal{R}$, then $\phi\left(\boldsymbol{v}_{p}^1, \ldots, \boldsymbol{v}_{p}^k\right)$ is defined.
>
> Furthermore,
>
> 1. **MULTILINEARITY**
> If $$\boldsymbol{v}^i_p = c \boldsymbol{u}_{p} + d \boldsymbol{w}_{p}$$ then $$\phi\left(\boldsymbol{v}^1_p, \ldots, \boldsymbol{v}^i_p, \ldots, \boldsymbol{v}_{p}^k\right) = c \phi\left(\boldsymbol{v}^1_p, \ldots, \boldsymbol{u}_{p}, \ldots, \boldsymbol{v}_{p}^k\right)+  d \phi\left( \boldsymbol{v}_{p}^1 , \ldots, \boldsymbol{w}_{p}, \ldots, \boldsymbol{v}_{p}^k \right)$$
> 2. **ALTERNATION**
> if $\boldsymbol{v}_{p}^i = \boldsymbol{v}^j_p$ for some $i \neq j$ then $$\phi\left(\boldsymbol{v}_{p}^1, \ldots, \boldsymbol{v}_{p}^i, \ldots, \boldsymbol{v}_{p}^j, \ldots, \boldsymbol{v}_{p}^k\right) = 0$$
> 3. **SMOOTHNESS**
> For any $k$ smooth vector fields $\boldsymbol{F}_{1}, \ldots, \boldsymbol{F}^k$  on $\mathcal{R}$, the function $e: \mathcal{R} \longrightarrow \mathbb{R}$ given by $e(p) = \phi\left(\boldsymbol{F}_{1}, \ldots, \boldsymbol{F}^k\right)$ is a smooth function.

>[!lemma] Lemma
> Let $\alpha$ be a multilinear function on $T_p \mathbb{R}^n$. The following are equivalent:
> 1. if $\boldsymbol{v}^i_p = \boldsymbol{v}_{p}^j$ for some $i \neq j$, then $$\alpha\left(\boldsymbol{v}_{p}^1, \ldots, \boldsymbol{v}^k_p\right)=0$$
> 2. For any $i \neq j$ $$\alpha\left( \boldsymbol{v}^1_p, \ldots, \boldsymbol{v}_{p}^i, \ldots \boldsymbol{v}_{p}^j, \ldots \boldsymbol{v}_{p}^k\right) = -\alpha\left( \boldsymbol{v}^1_p, \ldots, \boldsymbol{v}_{p}^j, \ldots \boldsymbol{v}_{p}^i, \ldots \boldsymbol{v}_{p}^k\right) $$
>
> Further, Suppose that $\alpha$ is multilinear and alternating. Let $\phi$ be any permutation (i.e. a reordering) of $\{1, \ldots, k\}$. Then $$\alpha\left(\boldsymbol{v}_{p}^{\sigma(1)}, \ldots, \boldsymbol{v}_{p}^{\sigma(k)}\right) = \text{sign}(\sigma)\alpha\left(\boldsymbol{v}_{p}^1, \ldots, \boldsymbol{v}_{p}^k\right)$$

>[!proof]-
> For the first part of the lemma, suppose $(1)$ is true and set $\boldsymbol{w}_{p} = \boldsymbol{v}_{p}^i + \boldsymbol{v}_{p}^j$, then
> $$\begin{align}
> \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{w}_p, \ldots, \boldsymbol{w}_p, \ldots, \boldsymbol{v}_p^k\right) &= \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i + \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^i + \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k\right) \\
> &= \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^i + \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k \right) + \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^i + \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k \right) \\
> &= \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^k \right) + \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k \right) \\
> &\;\,+\,\alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^k \right) + \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k \right) \\
> &= 0 + \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k \right) + \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^k \right) + 0\\
> &= \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k \right) - \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k \right) \\
> &= 0
>\end{align}$$
> which means $\boldsymbol{v}_{p}^i = \boldsymbol{v}_{p}^j$.
>
> Now suppose $\boldsymbol{v}_{p}^i = \boldsymbol{v}_{p}^j$ for some $i \neq j$. Lets denote those tangent vectors as $\boldsymbol{u}_{p}$, then
> $$\begin{align}
> \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{v}_p^k\right) &= \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k\right) \\
> &= -\alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k\right) \\
> &= -\alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{v}_p^k\right) \\
> &\implies  \\
> 0&= 2 \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{v}_p^k\right) \\
> 0&= \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{u}_p, \ldots, \boldsymbol{v}_p^k\right) \\
> 0&= \alpha\left(\boldsymbol{v}_p^1, \ldots, \boldsymbol{v}_p^i, \ldots, \boldsymbol{v}_p^j, \ldots, \boldsymbol{v}_p^k\right)
>\end{align}$$
> 
> The validity of the second part of the lemma follows immediately by the parity of permutations and the antisymmetric property of multilinear functions established in part (1).
> $$\tag*{$\square$}$$

>[!def] Definition Basic $k$-Forms $dx_I$
> 1. Let $I = \{i_1, \ldots, i_k\}$ be any ordered $k$-element subset of $\{1, \ldots, n\}$. Then $$dx_I = dx_{i_1}\ldots dx_{i_k}$$ is the $k$-form on $\mathcal{R}$ defined as follows. Let $p$ be any point of $\mathcal{R}$. Then:
>   - $dx_I\left(\boldsymbol{e}^{i_1}_{p}, \ldots, \boldsymbol{e}^{i_k}_{p}\right) = 1$
>   - $dx_I\left(\boldsymbol{e}^{j_1}_{p}, \ldots, \boldsymbol{e}^{j_k}_{p}\right) = 1$ for $J$ any ordered subset of $\{1, \ldots, n\}$ that is not a permutation of $I$.  
>
> 2. If $I = \{i_1, \ldots, i_k\}$ with not all elements distinct, then $$dx_I = dx_{i_1}\ldots dx_{i_k} = 0$$

>[!lemma] Corollary 
> Let $\sigma_0$ be any permutation of $I = \{i_1, \ldots, i_k\}$ and let $J = \sigma_0(I)$, i.e. $J = \{j_1, \ldots, j_k\}$ with $j_1 = \sigma_0(i_1), \ldots, \sigma_0(i_k)$. Then $$dx_I\left( \boldsymbol{e}^{j_1}, \ldots, \boldsymbol{e}^{j_k}\right) = \text{sign}(\sigma_0)$$

>[!proof]-
> This is just a special case of the previous lemma and the application of the previous definition.

>[!lemma] Lemma
> Let $\sigma$ be any permutation of $I=\{i_1, \ldots, i_k\}$. Then $$dx_{\sigma(I)} = \text{sign}(\sigma)dx_I$$

>[!proof]
> For $J=\{j_1, \ldots, j_k\}$ let us write $\boldsymbol{e}_{p}^J$ for the $k$-tuple $\left(\boldsymbol{e}_{p}^{j_1}, \ldots, \boldsymbol{e}_{p}^{j_k}\right)$. Using this notation it is equivalent to show
> $$dx_{\sigma(I)}\left( \boldsymbol{e}_{p}^{J}\right)=\text{sign}(\sigma)dx_I\left(\boldsymbol{e}_{p}^J\right)$$
> 1. Case
> Assume the elements of $J$ are not distinct, then obviously both sides of the equation are $0$.
>
> 2. Case
> Assume $J=\sigma_0(I)$ for some permutation $\sigma_0$. Then by the previous corollary
> $$dx_I\left(\boldsymbol{e}^J_p\right) = \text{sign}(\sigma_0)$$
> Let $I' = \sigma(I)$. Then
> $$\begin{align}
> J &= \phi_0(I) \\
> &= \phi_0(\phi^{-1}\phi(I)) \\
> &= \underbrace{(\phi_0 \phi^{-1})}_{= \phi_1} \underbrace{\phi(I)}_{=I'} \\
> &= \phi_1(I')
>\end{align}$$
> Applying the previous corollary to $I'$
> $$dx_{I'}\left(\boldsymbol{e}_{p}^J\right) = \text{sign}(\sigma_1)$$
> We know for the sign of a permutation
> $$\begin{align}
> \text{sign}(\sigma_1) &= \text{sign}(\sigma_0\sigma^{-1}) \\
> &= \text{sign}(\sigma_0) \text{sign}(\sigma^{-1})
>\end{align}$$
> Hence
> $$\begin{align}
> dx_{\sigma(I)}\left( \boldsymbol{e}_p^J\right) &= dx_{I'}\left(\boldsymbol{e}_p^J\right) \\
> &= \text{sign}(\sigma_0) \text{sign}\left(\sigma^{-1}\right) \\
> &= \text{sign}\left(\sigma^{-1}\right) dx_I\left(\boldsymbol{e}_p^J\right)
>\end{align}$$
> For any permutation $$\text{sign}\left(\sigma^{-1}\right) = \text{sign}(\sigma)$$
> $$\tag*{$\square$}$$

