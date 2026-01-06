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
> $$\boldsymbol{e}_{i_1} \wedge \boldsymbol{e}_{i_2} \wedge \dots \wedge \boldsymbol{e}_{i_p}$$
> 
> 1. **Selection (Distinctness):** According to the **Absorption** property, if any index is repeated (e.g., $i_1 = i_2$), then $\boldsymbol{e}_{i_1} \wedge \boldsymbol{e}_{i_1} = 0$. Therefore, to form a non-zero basis element, we must choose $p$ **distinct** indices from the set $\{1, \dots, n\}$.
> 2. **Ordering (Linear Dependence):** According to the **Antisymmetry** property, swapping any two vectors in the product flips the sign (e.g., $\boldsymbol{e}_1 \wedge \boldsymbol{e}_2 = -\boldsymbol{e}_2 \wedge \boldsymbol{e}_1$). Since $\boldsymbol{x}$ and $-\boldsymbol{x}$ are linearly dependent, they span the same $1$-dimensional subspace. This means that the specific order of the chosen indices does not create a new dimension; only the **set** of chosen indices matters.
> 3. **Counting:** The number of unique ways to choose a subset of $p$ distinct indices from a total of $n$ available indices, where the order of selection is irrelevant, is defined by the binomial coefficient:
> $$\binom{n}{p} = \frac{n!}{p!(n-p)!}$$
> 
> Thus, the number of linearly independent basis elements is $\binom{n}{p}$, which implies $\dim(V) = \binom{n}{p}$. $\square$

