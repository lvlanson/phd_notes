# Differential Forms in $\mathbb{R}^n$
## 1. Euclidean Spaces, Tanget Spaces, and Tangent Vector Fields

>[!def] Definition $\mathbb{R}^n$
> For $n \in \mathbb{N}$
> $$\mathbb{R}^n = \{(x_1, \ldots, x_n \,|\, x_i \in \mathbb{R}^n \}$$
> is the set of real points.

>[!def] Definition Vector Space
> For $n \in \mathbb{N}$
> $$\boldsymbol{R}^n = \left\{v = \begin{bmatrix}a_1 \\ \vdots \\ a_n \end{bmatrix}\; | \;a_i \in \mathbb{R}\right\}$$
> with vector addition and scalar multiplication accordingly defined.

>[!def] Definition Tangent Space
> Let $p=(x_1, \ldots, x_n) \in \mathbb{R}^n$. The tangent space $\boldsymbol{R}^n_p = T_p \mathbb{R}^n$ at $p$ is
> $$\boldsymbol{R}^n_p = \left\{\boldsymbol{v}_{p} = \begin{bmatrix} a_1 \\ \vdots \\ a_n \end{bmatrix}_{p} \; | \; a_i \in \mathbb{R}\right\}$$

>[!def] Definition Tangent Vector Field
> A *tangent vector field* $\boldsymbol{v}$ on $\mathbb{R}^n$ is a function $\boldsymbol{v}$ that associates to every point $p \in \mathbb{R}^n$ a tangent vector to $\mathbb{R}^n$ based at $p$, i.e., a tangent vector $\mathbb{v}_{p} \in T_p \mathbb{R}^n$. Thus we may write $\boldsymbol{v}(p) = \boldsymbol{v}_{p}$ for every $p \in \mathbb{R}^n$.

## 1.1 The Algebra of Differential Forms

>[!def] Definition Smooth Functions
> Let $\mathcal{R}$ be an open set in $\mathbb{R}^n$. Then
> $$C^{\infty}(\mathcal{R}) = \{f: \mathcal{R} \to \mathbb{R}\; | \; f \text{ has all partial derivatives of all orders at every point } p \in \mathcal{R}\}$$
> A function $f \in C^{\infty}(\mathcal{R})$ is said to be *smooth* on $\mathcal{R}$.

>[!def] Definition (monomial) $k$-forms, Differential Forms
>Let $\mathcal{R}$ be an open set in $\mathbb{R}^n$. Let $k \in \mathbb{N}$ be fixed. A **monomial $k$-form** on $\mathcal{R}$ is an expression
> $$fdx_{i_1}\ldots fdx_{i_k}$$
> where $f$ is a smooth function on $\mathcal{R}$.
> - a $k$-form on $\mathcal{R}$ is a sum of monomial $k$-forms on $\mathcal{R}$
> - a **differential form** $\phi$ on $\mathcal{R}$ is a $k$-form on $\mathcal{R}$ for some $k$ ($k$ is the degree of $\phi$)
> 
> We denote the set of all **$k$-forms** as
> $$\Omega^k(\mathcal{R}) = \{k\text{-forms on } \mathcal{R}\}$$
> and the set of all **differential forms** as
> $$\Omega^*(\mathcal{R}) = \{\text{differential forms on } \mathcal{R}\}$$

>[!remark] Notation
> - multi-index $I = (i_1, \ldots, i_k)$
> - therefore $dx_I = dx_{i_1} \ldots dx_{i_k}$

>[!example]
> 1. 0-form: $\phi = x^2y+ e^z$
> 2. 1-form: $\phi = x^2\,dx + (yz+1)\,dz$
> 3. 2-form: $\phi = xyz\,dy\,dz + xe^y\,dz\,dx$
> 4. 3-form: $\phi= (x^2+xyz+z^3)\,dx\,dy\,dz$

>[!def] Definition Operation of $k$-forms
> Let $\phi, \psi \in \Omega^k$, then the addition $+: \Omega^k \times \Omega^k \to \Omega^k$ of $k$-forms with same degree is done term by term. The addition is
> - commutative
> - associative
>
> The multiplication of differential forms $\cdot: \Omega^k \times \Omega^l \to \Omega^{k+l}$ is the concatenation
> $$dx_{I_1} \cdot dx_{I_2} = dx_{I_1} dx_{I_2}$$
> The multiplication is
> - associative
> - anticommutative, i.e. $dx_{i}dx_{j} = -dx_{j}dx_{i}$ for $i \neq j$

>[!lemma] Property 
> In the special case $i=j$ we get
> $$dx_i dx_i = -dx_i dx_i \implies dx_i^2=0$$

>[!lemma] Lemma
> 1. if $dx_I$ is any string with some $dx_i$ appearing more than once, then $dx_I = 0$
> 2. If $\phi$ is a $k$-form on an open set in $\mathbb{R}^n$ with $k>n$, then $\phi=0$
> 3. Let $\{i_1, \ldots, i_k\}$ be distinct. If $p:\{i_1, \ldots, i_k\} \to \{i_1, \ldots, i_k\}$ is any permutation, then
> $$dx_{p(i_1)} \ldots dx_{p(i_k)} = \text{sign}(p)dx_{i_1}\ldots dx_{i_k}$$
> 4. Let $\phi$ be a $k$-form and $\psi$ an $l$-form. Then $\phi \psi = (-1)^{kl}\psi \phi$
> 5. By $(4)$ if $k$ is odd, $\phi^2 = (-1)^{k^2} \phi^2 = -\phi^2$

^409e2a

>[!proof]-
> 1. Note that $dx_I$ looks something like
> $$ dx_I = dx_1 \ldots dx_i \ldots dx_i \ldots dx_n$$
> by transposing $dx_i$ we will have $dx_i$ being adjacent to each other, hence 
> $$\pm dx_i^2 = 0$$
> which is why the term $dx_I = dx_1 \ldots 0 \ldots dx_n = 0$ finally.
> 2. Since $k>n$ in $\mathbb{R}^n$ for the $k$-form, we will find some $dx_i$ which must appear at least double, since there are only $n$ variables to take the partial derivative of. Due to the relation of $(1)$ it must fault to zero.
> 3. Note, a permutation has positive sign, if the number of transpositions is even, and negative if the number of transpositions is odd. By the anticommutativity property of $k$-forms the relation follows immediately.
> 4. Suppose the degree of $\phi$ is even numbered, then no matter the degree of $\psi$ it takes an even number of transpositions to switch the differentials within the monomial $k$-forms. If $\psi$ is odd numbered, then there is a fixed point, which does not affect the number of transpositions. Therefore, if the degree of $\phi$ is even numbered, then the product $k \cdot l$ must be even numbered. By the anticommutativity property it follows an even number of transpositions will have an even number of $(-1)$ factors, thus $(-1)^{kl}=1$. Now supporse the degree of $\phi$ is odd while $\psi$ is also odd. To switch all positions between $\phi$ and $\psi$ we will need an odd number of transpositions, since each $k$-form provides an odd number of differentials to switch positions. Since odd times odd gives an odd number again, we get $(-1)^{kl} = -1$, which follows the logic of having an odd number of anticommutations.
> 5. As highlighted previously, in the case if $\phi, \psi$ are both odd, and the special case $\phi = \psi$ property (5) follows immediately.
> $$\tag*{$\square$}$$

>[!remark] Remark
> The algebra of differential forms is called **exterior algebra** and the product is called the **exteriror product**. Usually the terms $dx_i dx_j$ is written as wedge product $dx_i \land dx_j$. In the context of this book we omit this notation.

>[!def] Definition Hodge Star Operator 
> The Hodge $\star$-operator on $\mathbb{R}^n$ is a function that takes a $k$-form $\phi$ to an $(n-k)$-form $\star \phi$ defined as follows:
> 1. Let $I = \{x_{i_1}, x_{i_2}, \ldots, x_{i_k}\}$ be an ordered subset of $\{x_1, x_2, \ldots, x_n\}$, and let $J=\{x_{j_1}, x_{j_2}, \ldots, x_{j_{n-k}}\}$ be the complement of $I$ in $\{x_1, x_2, \ldots, x_n\}$, ordered so that
> $$dx_{i_1}\ldots dx_{i_k}dx_{j_1}\ldots dx_{j_{n-k}} = dx_1 dx_2 \ldots dx_n$$
> Then
> $$\star(dx_{i_1}\ldots dx_{i_k}) = dx_{j_1}\ldots dx_{j_{n-k}}$$
> 2. If $\phi= A_1dx_{I_1} + \ldots + A_mdx{I_m}$ is any $k$-form, then
> $$\star \phi =  \star A_1 dx_{I_1} + \ldots + \star A_m dx_{I_m}$$
> where $A_i$ are functions involved in $\phi$.

>[!remark]
> Note that the ordering of $J$ is established such that the standard ordering can be established. If there is no such ordering with respect to the anticommutative property by transposing odd number of times, then we have to add a minus sign.
> 
> To verify if the $\star$-operator has been computed correctly, we can verify for a basis $k$-form $\phi= dx_{I_1} \, dx_{I_2}\ldots dx_{I_k}$ that it must hold
> $$\phi (\star \phi) = dx_1 \, dx_2 \ldots dx_n$$
> with respect to permutations for the standard ordering (orientation).

>[!example] 
> 1. On $\mathbb{R}^1$
> $$\begin{align}
>   \star 1 &= dx \\
> \star dx & = 1
>\end{align}$$
> 2. On $\mathbb{R}^2$
> $$\begin{align}
> \star 1 &= dx\, dy \\
> \star dx &= dy \\
> \star dy &= -dx \\
> \star(dx \, dy) &= 1
>\end{align}$$
> Note the case of $\star dy$ feels special, because the result $-dx$ feels at first unexpected. Note that by the previous remark we require that
> $$\begin{align}
> dy\, (\star dy) &= dx dy
>\end{align}$$
> We know that 
> $$dx \, dy = -dy \, dx$$
> therefore it follows that
> $$\star dy = -dx$$
> 3. On $\mathbb{R}^3$
> $$\begin{align}
> \star 1 &= dx\, dy\, dz \\
> \star dx &= dy \, dz \\
> \star dy &= dx \, dz \\
> \star dz &= dx \, dy \\
> \star( dx \, dy) &= dz \\
> \star( dx \, dz) &= dy \\
> \star( dy \, dz) &= dx \\
> \star( dx \, dy \, dz) &= 1
>\end{align}$$
> Here we can higlight the relation $\star dy = dx \, dz$. We again have to establish the relation
> $$dy (\star dy) = dx \, dy \, dz$$
> Naturally, one would assume it makes sense to choose $\star y = dx \, dz$, but the following computation would give
> $$dy (\star y) = dy \, dx \, dz = -dx \, dy \, dz$$
> due to anticommutativity. Since the elements as a whole are odd, we can just switch two elements of our $\star$ computation to yield an ordering without the need of a minus sign, i.e.
> $$dy (\star) = dy \, dz \, dx = -dy \, dx \, dz = dx \, dy \, dz$$
> By definition we choose an ordering for $J$ such that the relation is established, which we can do. More precisely, we can finde a permutation $p$ such that $sgn(p) = 1$. If this is not possible we will prefix our $\star$-form with $sgn(p) = -1$ to fix the ordering issue.

>[!lemma] Lemma
> Let $\phi$ be a $k$-form on $\mathbb{R}^n$. Then
> $$\star (\star \phi) = (-1)^{k(n-k)}\phi$$
> In particular, if $n$ is odd, then $\star (\star \phi) = \phi$ for any $k$. If $n$ is even, then $\star (\star \phi) = \phi$ for $k$ even and $\star (\star \phi) = - \phi$ for $k$ odd.

>[!proof]
> Let $\phi = dx_I$ denote a monomial $k$-form on $\mathbb{R}^n$. For the relation $\phi (\star \phi) = dx_1 \ldots dx_n$ denote $\star \phi = dx_J$ such that $J$ is the complement set with respect to $I$ such that the relation holds. To compute $\star dx_J$ the following relation must hold
> $$dx_J (\star dx_J) = dx_1 \ldots dx_n$$
> Note, from $\star(\star \phi)) = \star (\star dx_J)$ we know the hodge dual of $dx_J$ has its indices in the complement of $J$, i.e. $I$. Therefore
> $$\star dx_J (\star (\star dx_J)) = \star dx_J dx_I$$
> By the previous [[#^409e2a | Lemma]] property (4) we know that
> $$\star dx_J dx_I = (-1)^{k(n-k)}dx_I \star dx_J$$
> Therefore we know that 
> $$\star(\star\phi)=\star(\star dx_I) = (-1)^{k(n-k)}dx_I = (-1)^{k(n-k)}\phi$$
> The relation of the exponent's oddity follows immediately from the realizations of $n$ and $k$.
> $$\tag*{$\square$}$$

## 1.2 Exterior Differentiation

>[!def] Definition Exterior Differentiation
> Let $A$ be a $0$-form, i.e. a function on an open set $\mathcal{R}$ in $\mathbb{R}^n$. Its exterior derivative $dA$ is the $1$-form on $\mathcal{R}$ 
> $$dA = A_{x_1}dx_1 + A_{x_2}dx_2+\ldots+ A_{x_n}dx_n$$
> where the subscripts denote partial derivatives.
>
> If $\phi=A_1dx_{I_1} + A_2dx_{I_2} + \ldots + A_mdx_{I_m}$ is a $k$-form on $\mathcal{R}$, then its exterior derivative $d \phi$ is the $(k+1)$-form
> $$d \phi = dA_1dx_{I_1} + dA_2dx_{I_2} + \ldots + A_mdx_{I_m}$$

>[!proposition]
> 1. If $$\phi= A$$ a $0$-form, then $$d \phi = A_x dx + A_y dy + A_z dz$$
> 2. If $$\phi = A dx + Bdy + C dz$$ a $1$-form, then $$d \phi = (C_y - B_z) dy \, dz + (A_z - C_x)dz\,dx + (B_x - A_y) dx\,dy$$
> 3. If $$\phi = A dy \, dz + B dz \, dx + C dx \, dy$$ a $2$-form, then $$d \phi = (A_x + B_y + C_z) dx \, dy \, dz$$
> 4. If $$\phi = A dx \, dy \, dz$$ a $3$-form, then $$d \phi = 0$$

>[!proof]
> 1. This is just the definition applied.
> 2. First we compute
> $$\begin{alignat}{2}
> dA\,dx &= (A_x\, dx + A_y\, dy + A_z\, dz) dx &= A_y\, dy\,dx + A_z\, dz\,dx \\
> dB\,dy &= (B_x\, dx + B_y\, dy + B_z\, dz) dy &= B_x\, dx\,dy + B_z\, dz\,dy \\
> dC\,dz &= (C_x\, dx + C_y\, dy + C_z\, dz) dz &= C_x\, dx\,dz + C_y\, dy\,dz
>\end{alignat}$$
> Putting them together and arranging for same differentials gives
> $$\begin{align}
>d(A\,dx + B\,dy + C\,dz) &=A_y \, dy\,dx + A_z\,dz\,dx + B_x\,dx\,dy+B_z\,dz\,dy + C_x\, dx\,dz+ C_y\,dy\,dz\\
> &= -A_y \, dx \,dy + B_x\,dx\,dy + A_z\, dz\,dx - C_x \,dz\,dx + C_y \,dy\,dz - B_z \,dy\,dz \\
> &= (B_x - A_y) dx \, dy + (A_z - C_x) dz\,dx + (C_y - B_z)dy\,dz
>\end{align}$$
>
> 3. Following the blueprint from (2) after computing $d \phi$ we get
> $$\begin{align}
> d(A\,dy\,dz + B\,dz\,dx + C\,dx\,dy) &= A_x \,dx\,dy\,dz + B_y \,dy\,dz\,dx + C_z \,dz\,dx\,dy \\
> &= A_x \,dx\,dy\,dz + B_y \,dx\,dy\,dz + C_z \,dx\,dy\,dz \\
> &= (A_x + B_y + C_z)dx\,dy\,dz
>\end{align}$$
> 4. Follows immediately from $k>n$, i.e. $4>3$.


>[!theorem]
> 1. (LINEARITY) Let $c_1$ and $c_2$ be constants and let $\phi_1$ and $\phi_2$ be $k$-forms. Then
> $$d(c_1 \phi_1 +  c_2 \phi_2) = c_1 d \phi_1 + c_2 d \phi_2$$
> 2. (LEIBNIZ RULE) Let $\phi$ be a $k$-form and let $\psi$ be an l-form. Then
> $$d(\phi \psi) = d(\phi) \psi + (-1)^k \psi(d \phi)$$

>[!proof]-
> 1. Follows immediately by the linearity of differentation.
> 2. Due to property (1) we can choose $\phi = Adx_I $ and $\psi = Bdx_J$ without loss of generality. Therefore compüuting the differential of the product gives
> $$\begin{align}
> d(\phi \psi) &= d(A\,dx_I \, B\,dx_J) \\
> &= d(AB)\,dx_I \,dx_J \\
> &= ((dA)B + A\,(dB)) \,dx_I \, dx_J \tag*{Product Rule} \\
> &= (dA)B \,dx_I\,dx_J + A\,(dB)\,dx_I\,dx_J
>\end{align}$$
> Note, we want to switch positions in the second term for $dB$ which is a $1$-form and $dx_I$. Since $dx_I$ is of degree $k$, we have to transpose $k$ times to achieve $(dB)\,dx_I = (-1)^k(dB)$. We therefore have
>$$\begin{align}
>d(\phi \psi) &= (dA)\,dx_I B\, dx_J + (-1)^k A\,dx_I (dB)\, dx_J\\
> &=\underbrace{d(A\,dx_I)}_{=d \phi}\, \underbrace{B \,dx_J}_{=\psi} + (-1)^k \underbrace{A\,dx_I}_{=\phi} \underbrace{d(B\,dx_J)}_{=d\psi} \\
> &= (d \phi) \psi + (-1)^k \phi (d \psi)
>\end{align}$$
> 

>[!theorem] Poincaré's Lemma
> Let $\phi$ be any differential form. Then
> $$d(d \phi) = 0$$

>[!proof]-
> The proof follows from the introduced computations. It suffices to show this for a single term due to linearity of the differential. Therefore, let $\phi=Adx_I$ denote a $k$-form. First we have
> $$\begin{align}
> d \phi &= (dA) \, dx_I \\
> &= A_{x_1}\,dx_1\, dx_I + A_{x_2} \, dx_2 \, dx_I + ... + A_{x_n} \, dx_n\, dx_I  
> \end{align}$$
> Now taking the second total derivative yields
> $$\begin{align}
> d \phi &= d(A_{x_1}\,dx_1\, dx_I\,+ A_{x_2} \, dx_2 \, dx_I + ... + A_{x_n} \, dx_n\, dx_I ) \\
> &= d(A_{x_1})\,dx_1\, dx_I\, + d(A_{x_2})  \, dx_2 \, dx_I + ... + d(A_{x_n}) \, dx_n\, dx_I \\
> &= \big(A_{x_1 x_1} \, dx_1 \, dx_I + A_{x_1 x_2} \, dx_2 \, dx_I+ ... + A_{x_1 x_{n-1}} dx_{n-1} \, dx_I + A_{x_1 x_n} dx_n \, dx_I\big) dx_1 \\
> &+ \big(A_{x_2 x_1} \, dx_1 \, dx_I + A_{x_2 x_2} \, dx_2 \, dx_I+ ... + A_{x_2 x_{n-1}} dx_{n-1} \, dx_I + A_{x_2 x_n} dx_n \, dx_I\big) dx_2 \\
> &\hspace{1.5em} \vdots \hspace{15em} \vdots \hspace{14em} \vdots \\
> &+ \big(A_{x_{n-1} x_1} \, dx_1 \, dx_I + A_{x_{n-1} x_2} \, dx_2 \, dx_I+ ... + A_{x_{n-1} x_{n-1}} dx_{n-1} \, dx_I + A_{x_{n-1} x_n} dx_n \, dx_I\big) dx_{n-1} \\
> &+ \big(A_{x_{n} x_1} \, dx_1 \, dx_I + A_{x_{n} x_2} \, dx_2 \, dx_I+ ... + A_{x_{n} x_{n-1}} dx_{n-1} \, dx_I + A_{x_{n} x_n} dx_n \, dx_I\big) dx_{n} \\
>\end{align}$$
> First, note that all terms $A_{x_i x_i} \,dx_i \,dx_j$ will vanish, because there is the outer factor $dx_i$ such that
> $$A_{x_i x_i} \, dx_i \, dx_j \, dx_i = - A_{x_i x_i} \, dx_i \, dx_i \, dx_j = 0$$
> The anticommutativity allows us to state $dx_i \, dx_j = -dx_j \, dx_i$, such that we can regroup
> $$\begin{align}
> d(d \phi) &= (A_{x_2 x_1} - A_{x_1 x_2})\, dx_1 \, dx_2 + (A_{x_3 x_1} \, dx_1 \, dx_3)  \\
> &+ \ldots + (A_{x_nx_{n-1}} - A_{x_{n-1} x_n})d_{x_{n-1} x_n}
>\end{align}$$
> Since A is a smooth function (at least 2 times differentiable in all variables) we can apply [Clairut's Theorem](https://www.youtube.com/watch?v=wLkXUmVKyi4&t=2s) which states for a two times differentiable function $f: \mathcal{R}^2 -> {\mathcal{R}'}^2$ in both variables on open sets $\mathcal{R}^2, {\mathcal{R}'}^2$, we can state
> $$\frac{\partial f}{\partial x \partial y} = \frac{\partial f}{\partial y \partial x}$$
> Hence all the differences $A_{x_i x_j} - A_{x_j x_i} = A_{x_i x_j} - A_{x_i x_j} = 0$ vanish, thus
> $$d(d \phi) = 0 \tag*{$\square$}$$

>[!def] Definition Closed Differential Forms
> If $\phi$ is a differential form with the property that $d \phi = 0$, then $\phi$ is **closed**.

>[!def] Definition Exact and Primitive Forms
> If $\phi$ is a differential form with the property that $\phi = d \psi$ for some form $\psi$, or $\phi=0$, then $\phi$ is **exact**. 
> 
> If $\phi = d \psi$, then $\psi$ is a **primitive** for $\phi$.

>[!lemma]
> 1. Let $\phi_1$ be any form and $\psi$ any closed form. Then $d(\phi_1 + \psi) = d \phi_1$.
> 2. Let $\phi_1$ and $\phi_2$ be any two forms with $d \phi_1 = d \phi_2$. Then $\phi_2 = \phi_1 + \psi$ for some closed form $\psi$.

>[!proof]-
> 1. Since $\psi$ is closed, we have $d \psi = 0$. Due to linearity of the differential we get
> $$d(\phi_1 + \psi) = d \phi_1 + d \psi = d \phi_1$$
> 2. We choose $\psi= \phi_2 - \phi_1$, therefore it holds
> $$\phi_2 = \phi_1 + \psi = \phi_1 + (\phi_2 - \phi_1) = \phi_2$$
> Now, notice that $\psi$ is closed, hence, 
> $$d \psi = d(\phi_2 - \phi_1) = d \phi_2 - d \phi_1 = 0$$
> Since $d \phi_1 = d \phi_2$
> $$\tag*{$\square$}$$

>[!lemma] 
> Let $\mathcal{R}$ be a connected region in $\mathbb{R}^n$. If $f$ is a function on $\mathcal{R}$ all of whose first partial derivatives are zero at every point of $\mathcal{R}$, then $f$ is contant on $\mathcal{R}$.

>[!proof]-
> For the proof we will show the validity on $\mathcal{R} \subseteq \mathbb{R}^2$ without loss of generality. The principle can be extended on any $n$-dimensional subspace. The proof will be structured as follows.
> 1. Assume $\mathcal{R}$ is convex, we fix the vertical coordinates $y_0 = y_1 = y$ and show that $f$ is constant
> 2. Assume $\mathcal{R}$ is convex, we fix the horizontal coordinates $x_0 = x_1 = x$ and show that $f$ is constant
> 3. Assume $\mathcal{R}$ is not necessarily convex but is connected, then we construct a path of line segments, such that each line segment gives the conclusion of $f$ being constant according to either (1) or (2). This concludes to $f$ being constant overall.
> 
> ---
>
> 1. Assume $y = y_0 = y_1$. Note the line segment from $(x_0, y)$ to $(x_1, y)$ lies completely in $\mathcal{R}$ since we assume here it is convex. By the mean value theorem we know there exists some $c \in [x_0, x_1]$ such that $$f(x_1, y) - f(x_0, y) = \frac{\text{d} f}{\text{d} x} (c, y)(x_1 - x_0)$$
> Since all partial derivatives are zero, we have
> $$f(x_1, y) -f(x_0, y) = 0 \implies f(x_1, y) = f(x_0, y)$$
> hence, $f$ is constant.
> 2. By making the assumption $x = x_0 = x_1$, we can follow the same blueprint and come to the exact same conclusion.
> 3. Now, since $\mathcal{R}$ is open and connected, it is path-connected. Fix two points $(x_0, y_0)$ and $(x_1, y_1)$. Since $\mathcal{R}$ is path-connected, there exists a continuously connected path $\gamma: [0,1] \to \mathcal{R}$ with $\gamma(0)=(x_0, y_0$ and $\gamma(1) = (x_1, y_1)$. <br>
>Since $\gamma([0,1])$ is compact, we can find a finite subcover of $\varepsilon$-balls with centers $p_i \in \gamma([0,1])$ covering $\gamma([0,1])$. We order the balls such that successive balls intersect along the path. Choosing points $(x_0,y_0) = p_0, p_1, \ldots, p_k = (x_1, y_1)$ with each consecutive pair $p_i, p_{i+1}$ lying in a common $\varepsilon$-ball, we obtain a finite chain connecting the two endpoints. <br>
>Since every ball is convex, the segment connecting $p_i$ and $p_{i+1}$ lies entirely inside that ball. By applying (1) or respectively (2) to the corresponding horizontal and vertical components of this segment, we can conclude that
> $$f(p_i) = f(p_{i+1})$$
> for each $i$. Thus due to (1)/(2) we have
> $$f(p_0) = f(p_1) = \ldots = f(p_k)$$
> and therefore $f(x_0, y_0) = f(x_1, y_1)$. Since the tow points were arbitrary, $f$ is constant on $\mathcal{R}$. $$\tag*{$\square$}$$

>[!Lemma] Corollary
> Let $f$ be a $0$-form, i.e., a function, on a connected region $\mathcal{R}$ in $\mathbb{R}^n$. Then $f$ is a closed $0$-form on $\mathcal{R}$ if and only if $f$ is constant on $\mathcal{R}$.

>[!proof]-
> 1. $\implies$
> If $f$ is constant, then all partial derivatives $f_x = 0$, hence $df = 0$ which is the condition for $f$ to be closed by definition.
>
> 2. $\Longleftarrow$
> If $f$ is a closed $0$-form, then $df = 0$. Since $\mathcal{R}$ is connected by the previous lemma $f$ must be constant.
> $$\tag*{$\square$}$$

>[!Lemma] Corollary 
> Every exact differential form is closed.

>[!proof]-
> If $\phi$ is exact, then we know there exists some differential form $\psi$ such that $\phi = d \psi$ or $\phi = 0$ which would be the trivial case.
>
> Now for $\phi$ to be closed it has to be true that $d \phi = 0$. By Poincaré's lemma we know
> $$d \phi = d(d \psi) = 0$$
> which is why $\phi$ is closed if $\phi$ is exact. $$\tag*{$\square$}$$

>[!example]
> Let $\phi = 5x^4y^2z^3 \,dx + 2x^5yz^3 \, dy + 3x^5y^2z^2 \, dz$. We know $\phi$ is exact, because there exists the primitive 
> $$\psi = x^5y^2z^3$$
> i.e. $\phi = d \psi$. Since $\phi$ is exact, we know by the previous corollary that, $d \phi = d(d \psi) = 0$, i.e. $\phi$ is closed.
>>[!example]- Computations
>>  
>> Let
>> $$
>> \omega
>> =
>> 5x^4y^2z^3\,dx
>> +
>> 2x^5yz^3\,dy
>> +
>> 3x^5y^2z^2\,dz.
>> $$
>> 
>> For $\omega = A\,dx + B\,dy + C\,dz$ we have
>> $$
>> d\omega
>> =
>> dA \wedge dx
>> +
>> dB \wedge dy
>> +
>> dC \wedge dz.
>> $$
>> 
>> Compute the partial derivatives.
>> 
>> $$
>> A = 5x^4y^2z^3
>> $$
>> $$
>> \frac{\partial A}{\partial x} = 20x^3y^2z^3,
>> \quad
>> \frac{\partial A}{\partial y} = 10x^4yz^3,
>> \quad
>> \frac{\partial A}{\partial z} = 15x^4y^2z^2.
>> $$
>> 
>> $$
>> dA
>> =
>> 20x^3y^2z^3\,dx
>> +
>> 10x^4yz^3\,dy
>> +
>> 15x^4y^2z^2\,dz.
>> $$
>> 
>> $$
>> dA \wedge dx
>> =
>> 10x^4yz^3\,dy\wedge dx
>> +
>> 15x^4y^2z^2\,dz\wedge dx.
>> $$
>> 
>> $$
>> B = 2x^5yz^3
>> $$
>> $$
>> \frac{\partial B}{\partial x} = 10x^4yz^3,
>> \quad
>> \frac{\partial B}{\partial y} = 2x^5z^3,
>> \quad
>> \frac{\partial B}{\partial z} = 6x^5yz^2.
>> $$
>> 
>> $$
>> dB
>> =
>> 10x^4yz^3\,dx
>> +
>> 2x^5z^3\,dy
>> +
>> 6x^5yz^2\,dz.
>> $$
>> 
>> $$
>> dB \wedge dy
>> =
>> 10x^4yz^3\,dx\wedge dy
>> +
>> 6x^5yz^2\,dz\wedge dy.
>> $$
>> 
>> $$
>> C = 3x^5y^2z^2
>> $$
>> $$
>> \frac{\partial C}{\partial x} = 15x^4y^2z^2,
>> \quad
>> \frac{\partial C}{\partial y} = 6x^5yz^2,
>> \quad
>> \frac{\partial C}{\partial z} = 6x^5y^2z.
>> $$
>> 
>> $$
>> dC
>> =
>> 15x^4y^2z^2\,dx
>> +
>> 6x^5yz^2\,dy
>> +
>> 6x^5y^2z\,dz.
>> $$
>> 
>> $$
>> dC \wedge dz
>> =
>> 15x^4y^2z^2\,dx\wedge dz
>> +
>> 6x^5yz^2\,dy\wedge dz.
>> $$
>> 
>> Using
>> $$
>> dy\wedge dx = -dx\wedge dy,
>> \quad
>> dz\wedge dx = -dx\wedge dz,
>> \quad
>> dz\wedge dy = -dy\wedge dz,
>> $$
>> all terms cancel, hence
>> $$
>> d\omega = 0.
>> $$
>

>[!remark]
> We concluded that 
> $$\text{differential form is exact } \implies \text{differential form is closed}$$
> but the reverse is not unconditionally true
> $$\text{differential form is closed } \centernot\implies \text{differential form is exact}$$

>[!lemma] 
> Let $$\phi = f^1(x_1, \ldots, x_n) \, dx_1 + f^2(x_1, \ldots, x_n)\, dx_2 + \ldots + f^n(x_1, \ldots, x_n) \, dx_n$$
> be a closed $1$-form defined on a connected region $\mathcal{R}$ in $\mathbb{R}^n$. Suppose that, for some $i$, $f^i(x_1, \ldots, x_n)$ is a function of $x_i$ alone, i.e., that $f^i(x_1, \ldots, x_n) =  g(x_i)$ for some function $g$ (especially if the $dx_i$ term is missing, i.e. $f^i = 0$). Then for every $j \neq i, f^j(x_1, \ldots, x_n)$ is a function of the remaining variables $x_1, \ldots, x_{i-1}, x_{i+1}, \ldots, x_n$, i.e., $$f^j(x_1, \ldots, x_n) = h^j(x_1, \ldots, x_{i-1}, x_{i+1}, \ldots, x_n)$$ for some function $h^j$.

>[!proof]-
> Write $$\phi = \psi + \rho$$
> with 
> $$\psi = f^1(x_1, \ldots, x_n) \, dx_1 + \ldots + f^{i-1}(x_1, \ldots, x_n) \, dx_{i-1} + f^{i+1}(x_1, \ldots, x_n)\, dx_{i+1} + \ldots + f^n(x_1, \ldots, x_n) \, dx_n$$
> and 
> $$\rho = f^i(x_1, \ldots, x_n) \, dx_i = g(x_i) \, dx_i$$
> Clearly, we have
> $$d \phi = d(\psi + \rho) = d \psi + d \rho = d \psi + 0 = d \psi$$
> Since $\phi$ is closed, we expect $d \phi = d \psi = 0$. Note that $d\psi$ is a 2-form, i.e. we find differential pairs $dx_s\, dx_t$ with $x, s \neq i$. Further note that $\psi$ misses out on the $dx_i$ term, so $d \psi$ lacks any contributions form differentiating $f^i$ (which is in $\rho$). Still, we know that $\frac{\partial f^i}{\partial x_j} = 0$ for $i \neq j$ since $f^i = g(x_i)$ does not depend on $x_j$. Explicitly
>$$d \psi = \sum_{j \neq i} \sum_{k=1}^{n}\frac{\partial f^j}{\partial x_k}dx_k\,dx_j$$ 
>to zero out on all the terms such as $f^j_{x_i}dx_i \, dx_j$ we require to find the corresponding counter differential $f^i_{x_j}dx_j \, dx_i$ which by definition of $g(x_i)$ is missing. Hence $f^j_{x_i}=0$ and for that reason $\psi$ is independent of $x_i$. $$\tag*{$\square$}$$

>[!algo] Method
> Denote
> - 1-form $\phi = \sum_{i=1}^{n} f^i(\boldsymbol{x}) \, dx_i$ with $\phi$ is closed, i.e. $d \phi = 0$
> - primitive of $\phi$ as $d \psi = \phi$
>
>>[!example]- Example 
>> Let $$\phi(x,y) = \underbrace{(2xy^3 + 4x^3)}_{A_{x}} \, dx + \underbrace{(3x^2y^2 + 2y)}_{A_y}\, dy$$
>
> Compute the antiderivative $$F^1(\boldsymbol{x}) = \int f^1(\boldsymbol{x}) \, dx_1$$
> We yield
> $$\begin{align} 
> d \psi_1 &= \sum_{i=1}^{n} F^1_{x_i} \, dx_i  \\
> &= f^1\, dx_1 + \sum_{i=2}^{n}F^1_{x_i} \, dx_i \\
> &= f^1\, dx_1 + d (c(x_2, ..., x_n)) \\
> &= f^1 \, dx_1
>\end{align}$$
> 
> where $c(x_2, \ldots, x_n)$ is the integration constant with respect to $x_1$ of $f^1$. By design the integration constants **must** be independent of $x_1$, such that it vanishes when taking the derivative with respect to $x_1$. 
>
>>[!example]- Example Continued
>> Version 1:
>> $$\begin{align}
>> \psi_1 &= \int A_x \, dx \\
>> &= \int 2xy^3 + 4x^3 \, dx \\
>> &= x^2y^3 + x^4 + c(y)
>>\end{align}$$
>> with $c(y)$ being a function of $y$.
>> 
>> --- 
>> Version 2:
>> $$\begin{align}
>> \psi_2 &= \int A_y \,dy \\
>> &= \int 3x^2y^2 + 2y \, dy \\
>> &= x^2 y^3 + y^2 + c(x) 
>>\end{align}$$
>> with $c(x)$ being a function of $x$.
>
> By construction we have
> $$\phi - d \psi_1 = \underbrace{\left(f^2 - F^1_{x_2}\, \right)}_{g^2(x_2, \ldots, x_n)} dx_2+ \ldots + \underbrace{\left(f^n - F^1_{x_n}\right)}_{g^n(x_2, \ldots, x_n)}\, dx_n$$
>
> and it follows
> $$\begin{align}
> d(\phi - d \psi_1) = d \phi - d(d \psi_1) = 0-0 = 0
>\end{align}$$
> hence we can make use of the preceding lemma and construct a function $g^j$ with $j \neq 1$ such that $g^j$ is independent of $x_1$.
> 
> Do the same procedure for $g$, i.e. compute the antiderivative of $g^2$ such that the partial derivative $G^2_{x_2} = g_{x_2}$ and we set $\psi_2 = G^2$. At the end of the procedure we get
> $$\phi - d(\psi_1 + \psi_2 + \ldots + \psi_n) = 0$$ 
> and therefore we have found the primitive of $\phi$ which is $$\psi = \sum_{i=1}^{n} \psi_i$$
>>[!example] Example Finished
>> Note that $\psi = \psi_1 + \psi_2$ in this example.
>> Version 1:
>> First we compute as highlighted the partial derivative of $\psi_1$ with respect to $y$ because $$d \psi_1 = \frac{\partial \psi_1}{\partial x} + \frac{\partial \psi_1}{\partial y} = A_x\, dx + \frac{\partial \psi_1}{\partial y} $$
>> we have
>> $$\frac{\partial \psi_1}{\partial y} = \frac{\partial}{\partial y} x^2y^3 + x^4 + c(y) = 3x^2 y^2 + c'(y)$$
>> where $c'(y)$ is the derivative of the integration constant (w.r.t. $x$) of $A_x$. To determine $g(y)$, we compute 
>> $$\begin{align}
>> g(y) &= \left(A_y - \frac{\partial \psi_1}{\partial y}\right) \, dy \\
>> &= \left( 3x^2y^2 + 2y - (3x^2 y^2 + c'(y)) \right) \, dy \\
>> &= (2y - c'(y)) \, dy
>>\end{align}$$
>> Since $g(y)$ is independent of $x$, we can simply integrate with respect to $y$, i.e.
>> $$\begin{align}
>> \int g(y) \, dy &= \int 2y - c'(y) \,dy = y^2 - c(y)
>>\end{align}$$
>> Since 
>> $$\phi - d \psi_1 = (d \psi) - d \psi_1 = (d \psi_1 + d \psi_2) - d \psi_1 = d \psi_2$$
>> we know that $g(y) = d \psi_2$, thus $G(y) = \psi_2$. Without loss of generality we choose $c(y) = 0$, and have
>> $$\psi = \psi_1 + \psi_2 = \underbrace{x^2y^3 + x^4}_{\psi_1} + \underbrace{y^2}_{\psi_2}$$
>> ---
>> Version 2:
>> We take a shortcut here
>> Note that $$\frac{\partial \psi}{\partial x} = \frac{\partial}{\partial x} x^2 y^3 + y^2 + c(x) = 2xy^3 + c'(x)$$
>> We know that the derivative of the integration constant is a function of $x$, looking at $A_x$ we see that $$c'(x) = 4x^3$$
>> Integrating with respect to $x$, we get $$\int c'(x) \, dx = \int 4x^3 \, dx = x^4$$
>> Therefore we get $$\psi = \psi_1 + \psi_2 = x^2 y^3 + y^2 + x^4$$

>[!lemma]
> Let $\phi$ be an $n$-form on $\mathbb{R}^n$. In this case, $\phi$ is automatically closed and can be written in the form $$\phi= f(x_1, \ldots, x_n) \, dx_1 \ldots dx_n$$
> Let $F(x_1, \ldots, x_n)$ be any antiderivative of $f(x_1, \ldots, x_n)$ with respect to the variable $x_1$. Let
> $$\psi = F(x_1, \ldots, x_n) dx_2\, \ldots dx_n$$
> Then $\phi = d \psi$

>[!proof]-
> We simply compute
> $$\begin{align}
> d \psi &= dFdx_2 ... dx_n \\
> &= \left(\sum_{i=1}^{n} F_{x_i}dx_i\right) dx_2 ... dx_n\\
> &= f dx_1 \, dx_2 \, ... \, dx_n + 0 + ... + 0 \\ 
> &= \phi \tag*{$\square$}
>\end{align}$$

## 1.3 The Fundamental Correspondence

>[!def] Definition Smooth Tangent Vector Field
> Let $f^1(x_1, \ldots, x_n), f^2(x_1, \ldots, x_n), \ldots, f^n(x_1, \ldots, x_n)$ be smooth function defined on a region $\mathcal{R} \subseteq \mathbb{R}^n$. Then
> $$\mathbb{v} = f^1(x_1, \ldots, x_n) \boldsymbol{e}^1 + f^2(x_1, \ldots, x_n) \boldsymbol{e}^2+ \ldots + f^n(x_1, \ldots, x_n) \boldsymbol{e}^n$$
> is a **smooth tangent vector field** on $\mathcal{R}$.

>[!example]
> 1. $\boldsymbol{F} = \underbrace{x^2}_{f^1}\boldsymbol{e}^1 + \underbrace{(yz + 1)}_{f^2}\boldsymbol{e}^2$ is a smooth vector field on $\mathcal{R} = \mathbb{R}^3$
> 2. $\boldsymbol{G} = \underbrace{\left( \frac{xy}{z} \right)}_{f^1}\boldsymbol{e}^1 + \underbrace{xe^y}_{f^2}\boldsymbol{e}^2 + \underbrace{2}_{f^3}\boldsymbol{e}^3$ is a smooth vector field on $\mathcal{R} = \mathbb{R}^3 - z$-axis

>[!def] Definition Gradient and Divergence
> 1. Let $f = f(x_1, x_2, \ldots, x_n)$ be a smooth function on a region $\mathcal{R} \subseteq \mathbb{R}^n$. Its **gradient** $\textbf{grad}(f)$ is the tangent vector field on $\mathcal{R}$ given by $$\textbf{grad}(f) = f_{x_1} \boldsymbol{e}^1 + f_{x_2} \boldsymbol{e}^2 + \ldots + f_{x_n} \boldsymbol{e}^n$$
> with $f_{x_i} = \frac{\partial f}{\partial x_i}$
> 2. Let $$\boldsymbol{F} = \sum_{i=1}^{n}f^i(x_1, \ldots, x_n) \boldsymbol{e}^i$$
> be a smooth tangent vector field on $\mathcal{R}$. Its divergence $div(\boldsymbol{F})$ is the smooth function on $\mathcal{R}$ given by
> $$\text{div}(\boldsymbol{F}) = \sum_{i=1}^{n}f^i_{x_i}(x_1, \ldots, x_n)$$


