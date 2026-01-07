### Geometric Algebra

The **wedge product** is a fundamental algebraic operation that takes two vectors and "wedges" them together to form a bivector, representing a directed area segment spanned by those vectors. In geometric algebra, this operation generalizes the concept of multiplication to higher dimensions, allowing for the construction of oriented volumes (trivectors) and hyper-volumes

![[Figures/exterior_product.png|center|400]]

The area in the image can be expressed as the wedge product, i.e.

$$\boldsymbol{u} \land \boldsymbol{v} = A$$
which is the area of the parallelogram. To further highlight this example, let us illustrate how to actually compute such a wedge-product for the the given vectors. We will rewrite the vectors $\boldsymbol{u} = u_1 \boldsymbol{e}_{1} + u_2 \boldsymbol{e}_{2}$ and $\boldsymbol{v} = v_1 \boldsymbol{e}_{1} + v_2 \boldsymbol{e}_{2}$ where $\boldsymbol{e}_{i}$ are some basis vectors of $V$. Now, demonstrating the wedge-product, we get

$$\begin{align}
\boldsymbol{u} \land \boldsymbol{v} &= (u_1 \boldsymbol{e}_1 + u_2 \boldsymbol{e}_2) \land (v_1 \boldsymbol{e}_{1} + v_2 \boldsymbol{e}_{2}) \\
&= u_1 \boldsymbol{e}_1 \land (v_1 \boldsymbol{e}_1 + v_2 \boldsymbol{e}_2) + u_2 \boldsymbol{e}_2\land(v_1 \boldsymbol{e}_1 + v_2 \boldsymbol{e}_2) \tag{Distributivity over $\boldsymbol{u}$}\\
&= (u_1 \boldsymbol{e}_1 \land v_1 \boldsymbol{e}_1) + (u_1 \boldsymbol{e}_1 \land v_2 \boldsymbol{e}_2) + (u_2 \boldsymbol{e}_2 \land v_1 \boldsymbol{e}_1) + (u_2 \boldsymbol{e}_2 \land v_2 \boldsymbol{e}_2) \tag{Distributivity over $\boldsymbol{v}$} \\
&= u_1v_1(\boldsymbol{e}_1 \land \boldsymbol{e}_1) + u_1 v_2(\boldsymbol{e}_1 \land \boldsymbol{e}_2) + u_2v_1 (\boldsymbol{e}_2 \land \boldsymbol{e}_1) + u_2v_2(\boldsymbol{e}_2 \land \boldsymbol{e}_2) \tag{Wedge Linearity} \\
&= \cancel{u_1v_1(\boldsymbol{e}_1 \land \boldsymbol{e}_1)} + u_1 v_2(\boldsymbol{e}_1 \land \boldsymbol{e}_2) + u_2v_1 (\boldsymbol{e}_2 \land \boldsymbol{e}_1) + \cancel{u_2v_2(\boldsymbol{e}_2 \land \boldsymbol{e}_2)} \tag{Antisymmetry} \\
&= u_1v_2(\boldsymbol{e}_1 \land \boldsymbol{e}_2) + u_2v_1(\boldsymbol{e}_2 \land \boldsymbol{e}_1) \\
&= u_1v_2 (\boldsymbol{e}_1 \land \boldsymbol{e}_2) - u_2v_1 (\boldsymbol{e}_1 \land \boldsymbol{e}_2) \tag{Antisymmetry}\\
&= (u_1v_2 - u_2v_1)(\boldsymbol{e}_1 \land \boldsymbol{e}_2)
\end{align}$$
which is the formula for the determinant of the Matrix $[\boldsymbol{u}\boldsymbol{v}]$. Note, that $\boldsymbol{e}_{1} \land \boldsymbol{e}_{2}$ **spans the unit square**. We will quickly define the wedge product, and then have short insight on how the antisymmetric operations worked.

>[!def] Definition Wedge Product
> The wedge product is a multiplicative operation on $p$-vectors in $\bigwedge^p$ generating geometric exteriors. Let $\boldsymbol{a} \in \bigwedge^k, \boldsymbol{b} \in \bigwedge^t$, where a $1$-vector is just a conventional vector. Then the wedge product 
> $$\boldsymbol{a} \land \boldsymbol{b} \in \bigwedge^{k+t}$$
> fulfills the following properties for additional $p$-vectors $\boldsymbol{c}, \boldsymbol{d}$
> $$\begin{align}
> (\boldsymbol{a} \land \boldsymbol{b}) \land \boldsymbol{c} &= \boldsymbol{a} \land (\boldsymbol{b} \land \boldsymbol{c}) \tag{Associativity}\\
> (\boldsymbol{a} + \boldsymbol{b}) \land (\boldsymbol{c} + \boldsymbol{d}) &= (\boldsymbol{a} \land \boldsymbol{c}) + (\boldsymbol{a} \land \boldsymbol{d}) + (\boldsymbol{b} \land \boldsymbol{c}) + (\boldsymbol{b} \land \boldsymbol{d}) \tag{Bilinearity}\\
> \boldsymbol{a} \land \boldsymbol{b} &= -\boldsymbol{b} \land \boldsymbol{a} \tag{Antisymmetry}\\
> \boldsymbol{a} \land \boldsymbol{a} &= 0 \tag{Absorption}
>\end{align}$$

>[!remark] Remarks
> - consider $\boldsymbol{a}, \boldsymbol{b}$ $1$-vector, i.e. simple vectors, then the result of $\boldsymbol{a} \land \boldsymbol{b}$ is a bivector or also a $2$-vector
>   - elements of $\bigwedge^k$ are refered from now on as $p$-vectors
> - the bilinearity follows simply from distributive properties
> - the absorption follows from the antisymmetry, because if $\boldsymbol{a} \land \boldsymbol{a} = -\boldsymbol{a} \land \boldsymbol{a}$ then the only solution possible is $\boldsymbol{a} \land \boldsymbol{a} = 0$
> - each $V = \bigwedge^i$ is a vector space in its own right
> - each $V = \bigwedge^i$ completely addresses the space on which the exterior algebra is defined
>   - assume $\dim(V) = 3$ and $\{\boldsymbol{e}_{1}, \boldsymbol{e}_{2}, \boldsymbol{e}_{3}\}$ are basis vectors of $V$
>   - assume we have $\bigwedge^2$ over $V$, then a basis would address all the planes ($i=2$) available in $V$, hence
>   - the basis would be $\boldsymbol{B}=\{\boldsymbol{e}_{1} \wedge \boldsymbol{e}_{2}, \boldsymbol{e}_{1} \wedge \boldsymbol{e}_{3}, \boldsymbol{e}_{2} \wedge \boldsymbol{e}_{3}\}$
>   - note that the basis is all the permutations of length $2$ of $3$ available base vectors, which leads to the following lemma

>[!lemma] Lemma Dimensionality of the Exterior Algebra
> Let $V=\bigwedge^i$ denote a exterior algebra over the vector space $W$ with $\dim(W)=n$. It follows that
> $$\dim(V) = \binom{n}{p}$$


>[!proof] Proof
> Let $\{ \boldsymbol{e}_{1}, \ldots, \boldsymbol{e}_{n}\}$ denote the basis vectors of the $n$-dimensional vector space $W$. Any basis element of the exterior algebra $V = \bigwedge^p W$ is constructed by the wedge product of $p$ basis vectors:
> $$\boldsymbol{e}_{1} \wedge \boldsymbol{e}_{2} \wedge \dots \wedge \boldsymbol{e}_{p}$$
> 
> 1. Selection (Distinctness): According to the **Absorption** property, if any index is repeated (i.e., $\boldsymbol{e}_{i} = \boldsymbol{e}_{j}$ for $i \neq j$), then $\boldsymbol{e}_{i} \wedge \boldsymbol{e}_{i} = 0$. Therefore, to form a non-zero basis element, we must choose $p$ **distinct** indices from the set $\{1, \dots, n\}$.
> 2. Ordering (Linear Dependence): According to the **Antisymmetry** property, swapping any two vectors in the product flips the sign (e.g., $\boldsymbol{e}_1 \wedge \boldsymbol{e}_2 = -\boldsymbol{e}_2 \wedge \boldsymbol{e}_1$). Since $\boldsymbol{x}$ and $-\boldsymbol{x}$ are linearly dependent, they span the same $1$-dimensional subspace. This means that the specific order of the chosen indices does not create a new dimension; only the **set** of chosen indices matters.
> 3. **Counting:** The number of unique ways to choose a subset of $p$ distinct indices from a total of $n$ available indices, where the order of selection is irrelevant, is defined by the binomial coefficient:
> $$\binom{n}{p} = \frac{n!}{p!(n-p)!}$$
> 
> Thus, the number of linearly independent basis elements is $\binom{n}{p}$, which implies $\dim(V) = \binom{n}{p}$. $\square$

>[!property] Linear Independence
> Let $\boldsymbol{e}_{i} \in V$. We say $\boldsymbol{e}_{i}$ are linearly dependent if
> $$\boldsymbol{e}_{1} \wedge \ldots \wedge \boldsymbol{e}_{p} = 0$$
> otherwise they are linearly independent.

>[!remark]
> This originates from the fact, that if one of the base vectors is just a linear combination of another. Let therefore $\boldsymbol{u}, \boldsymbol{v} \in V$ denote vectors and $\alpha \in \mathbb{K}$ a scalar of the underlying field. Also we define $\boldsymbol{u}=\alpha \boldsymbol{v}$. Then for whatever other vectors we are using, if $\boldsymbol{u}, \boldsymbol{v}$ are factors of the wedge product, we get $$\begin{align}
> \boldsymbol{u} \wedge \boldsymbol{v} &= \alpha \boldsymbol{v} \wedge \boldsymbol{v} \\
> &= \alpha 0 \\
> &= 0
>\end{align}$$
> which nullifies any other wedge factors.

>[!def] Definition Exterior Algebra/Grassman Algebra
> Let $\wedge$ denote the wedge product/exterior product and $\bigwedge^p$ the space of all $p$-vectors with $V$ being the underlying vectorspace with $\dim(V) = n$. We call the space $$\wedge V := \bigoplus_{k=0}^n \bigwedge^k$$ an **exterior algebra** or the **Grassmann algebra**.

>[!remark] Remark
> The fact that the exterior algebra allows to arbitrary "multiply"/wedge vectors allows the space itself to be called an **algebra**. The operation which is equipped to this very specific space is referred to as **wedge product** or **exterior product**.
>
> Note, that if one multiplies more than $n$ $1$-vectors over an $n$-dimensional vector space, one would always yield $0$ due to the absorption property. This is why one can say, that the exterior product has a ceiling in the number of factors it can process.
> 
> As a last note, the exterior algebra is usually defined over a field $\mathbb{K}$. For the context of the book it is sufficient to define it over $V$ since $V$ is implicitly defined over a field $\mathbb{K}$.

>[!def] Definition Dual Space of a Vector Space
> Let $V$ denote a vector space. Then the dual (space) of $V$ denoted as $V^*$ is the set of all linear functionals $\boldsymbol{f} \in V^*$
> $$\boldsymbol{f}: V \to \mathbb{R}$$

>[!remark] Remark
> The dual space of the exterior algebra is an exterior algebra itself. We will show next why this is true.

>[!corollary] The Dual Space is a Vector Space
> The dual space $V^*$ of vector space $V$ is a vector space itself.

>[!proof]
> Let $\boldsymbol{\widetilde{\alpha}}, \boldsymbol{\widetilde{\beta}} \in V^*$ and $\boldsymbol{v}, \boldsymbol{w} \in V$ and $a,b \in \mathbb{R}$. Since the element of $V^*$ are linear functionals, the vector space axioms follow immediately from the properties of linearity, i.e.
> $$\begin{align}
> \boldsymbol{\widetilde{\alpha}}(a \boldsymbol{v} + b \boldsymbol{w}) &= a \boldsymbol{\widetilde{\alpha}}(\boldsymbol{v}) + b \boldsymbol{\widetilde{\alpha}}(\boldsymbol{w}) \\
> (\boldsymbol{\widetilde{\alpha}} + \boldsymbol{\widetilde{\beta}}) (\boldsymbol{v}) &= \boldsymbol{\widetilde{\alpha}}(\boldsymbol{v}) + \boldsymbol{\widetilde{\beta}}(\boldsymbol{v}) \\
> (a \boldsymbol{\widetilde{\alpha}})(\boldsymbol{v}) &= a \boldsymbol{\widetilde{\alpha}} (\boldsymbol{v})
>\end{align} $$

>[!remark] Notation Convention: Indices, Duality, and Variance
> In the context of Exterior Algebra and Discrete Calculus, the position of an index (superscript vs. subscript) is a functional label, not an arithmetic operation.
>
> ### 1. Superscripts $\neq$ Powers
> Unlike standard algebra, an upper index is almost never an exponent. 
> - $v^2$ refers to the **second component** of vector $v$, not $v \cdot v$.
> - $e^j$ refers to the **$j$-th dual basis element**.
> - Actual powers are typically clarified with parentheses: $(v^j)^2$.
>
> ### 2. Primal vs. Dual Basis
> The index position distinguishes between the geometric object and its "measurer":
> - **Primal Basis ($e_i$):** Represented with **subscripts**. These are the physical vectors/edges of your space (the "arrows").
> - **Dual Basis ($e^j$):** Represented with **superscripts**. These are the 1-forms (the "rulers") that evaluate the primal vectors via the relationship: $\langle e^j, e_i \rangle = \delta^j_i$.
>

>[!definition] Definition Dual Component Extractors
> Let $\boldsymbol{\widetilde{\sigma}}^i \in V^*$ denote the linear functional, such that for $\boldsymbol{v} \in V$
> $$\boldsymbol{\widetilde{\sigma}}^i(\boldsymbol{v}) = v_i$$
> i.e. giving us the $i$-th component of $\boldsymbol{v}$.

>[!corollary] Corollary The Dual Basis
> Let $\boldsymbol{\widetilde{\sigma}}^i \in V^*$ denote the $i$-th component extractor and $\boldsymbol{e}_{j} \in V$ a basis Vector of $V$. The set of all
> $$\boldsymbol{\widetilde{\sigma}}^i(\boldsymbol{e}_{i}) := \boldsymbol{\widetilde{\sigma}}^i$$
> for all $1 < i < \dim(V)$ form a basis of the dual space.

>[!proof]
> First we need to show, that the vectors $\boldsymbol{\widetilde{\sigma}}^i$ are linearly indepent. Therefore, let $\boldsymbol{e}_{i} \in V$ a basis of $V$, which are by definition linearly independent. Therefore let $\lambda \in \mathbb{K}\setminus\{0\}$
> $$\begin{align}
> \sum_{i=1}^{n} \lambda_i \boldsymbol{\widetilde{\sigma}}^i(\boldsymbol{e}_i) &= 0 \\
> \sum_{i=1}^{n} \boldsymbol{\widetilde{\sigma}}^i(\lambda_i \boldsymbol{e}_i) &= 0 \\
>\end{align}$$
> Since $\boldsymbol{e}_{i}$ are linearly independent, the only solution solving the equation is $\lambda_i = 0$ for all $i$.
>
> Now we need to show, that any $\boldsymbol{\widetilde{\alpha}} \in V^*$ can be expressed as a linear combination of the assumed dual basis. Therefore let $\boldsymbol{v} \in V$ denote an arbitrary vector in $V$ which can be expressed as a linear combination of the basis vectors $\boldsymbol{e}_{i}$. We can express 
>$$\boldsymbol{v} = \sum_{i=1}^{n} v_i \boldsymbol{e}_{i} \tag{1}$$
> and therefore $v_i = \boldsymbol{\widetilde{\sigma}}^i(v_i \boldsymbol{e}_{i})$. Since $(1)$ is the unique linearcombination of $\boldsymbol{v}$, then
> $$\sum_{i=1}^{n} v_i \boldsymbol{\widetilde{\sigma}}^{i}$$
> represents a unique linear combination in the dual space. By setting 
> $$\boldsymbol{\widetilde{\alpha}} = \sum_{i=1}^{n}v_i \boldsymbol{\widetilde{\sigma}}^i$$
> we can represent any $\boldsymbol{\widetilde{\alpha}}\in V^*$.
>
> Therefore the set $\{\boldsymbol{\widetilde{\sigma}}^{i}\}_{i=1}^n$ form a basis of $V^*$ $$\tag*{$\square$}$$


> Let $\boldsymbol{\phi} \in V^*$ be an arbitrary linear functional. Let $a_i = \boldsymbol{\phi}(\boldsymbol{e}_i)$ be the scalars produced when $\boldsymbol{\phi}$ acts on the primal basis. For any $\boldsymbol{v} = \sum v^i \boldsymbol{e}_i$, we have by linearity:
> $$\boldsymbol{\phi}(\boldsymbol{v}) = \boldsymbol{\phi}\left(\sum v^i \boldsymbol{e}_i\right) = \sum v^i \boldsymbol{\phi}(\boldsymbol{e}_i) = \sum v^i a_i$$
> Since $v^i = \boldsymbol{\sigma}^i(\boldsymbol{v})$, we can rewrite this as:
> $$\boldsymbol{\phi}(\boldsymbol{v}) = \sum a_i \boldsymbol{\sigma}^i(\boldsymbol{v}) = \left(\sum a_i \boldsymbol{\sigma}^i\right)(\boldsymbol{v})$$
> Since this holds for all $\boldsymbol{v}$, $\boldsymbol{\phi} = \sum a_i \boldsymbol{\sigma}^i$. Thus, the set spans $V^*$. $\square$
