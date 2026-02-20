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

>[!remark] Notation Convention: Indices 
> We use the following notational convention:
> If we speak about **vectors from a vector space**:
> - vectors which describe the direction: **subscript**, i.e. $\boldsymbol{e}_{1}, \boldsymbol{e}_{2}, ...$
> - scalars which describe the scaling of a vector: **superscript**, i.e. $v^1 \boldsymbol{e}_{1} + v^2 \boldsymbol{e}_{2}$
> 
> If we speak about **forms from the dual space**:
> - vectors/forms which describe the evaluation of an $p$-vector: **superscript**, i.e. $\boldsymbol{\widetilde{\sigma}}^1, \boldsymbol{\widetilde{\sigma}}^2$
> - scalars which describe the scaling of the form: **subscript**, i.e. $\omega_1 \boldsymbol{\widetilde{\sigma}}^1 + \omega_2 \boldsymbol{\widetilde{\sigma}}^2$
> 
> The notation has a pragmatical purpose which is:
> - if you see alternating pairings of scalar and vectors, then those describe an object such as
>   - a vector, i.e. $\sum_{i=1}^{n}v^i \boldsymbol{e}_{i}$
>   - a form , i.e. $\sum_{i=1}^{n} \omega_i \boldsymbol{\widetilde{\sigma}}^i$
> - if you see pairings of scalars of alternating index levels, then this represents an evaluation of a vector over a form, i.e. let $\boldsymbol{v}= v^i \boldsymbol{e}_{i}$ and $\boldsymbol{\widetilde{\omega}}=\omega_j \boldsymbol{\widetilde{\sigma}}^j$. Then 
> $$\begin{align}
> \boldsymbol{\widetilde{\omega}}(\boldsymbol{v}) &= \sum_{i=1}^{n} \omega_i v^i
>\end{align}$$

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
> Mapping $\boldsymbol{v}$ yields
> $$\begin{align}
\boldsymbol{\widetilde{\alpha}}(\boldsymbol{v}) &= \boldsymbol{\widetilde{\alpha}}\left( \sum_{i=1}^{n} v^i \boldsymbol{e}_i\right)\\
> &= \sum_{i=1}^{n}v^i \boldsymbol{\alpha(\boldsymbol{e}_i)} \\
> &= \sum_{i=1}^{n}v^i a_i
>\end{align}$$
> Since $\boldsymbol{\widetilde{\sigma}}_{i}(\boldsymbol{v}) = v_i$ we have
> $$\begin{align}
> \boldsymbol{\widetilde{\alpha}}(\boldsymbol{v}) &= \sum_{i=1}^{n}a_i \boldsymbol{\widetilde{\sigma}}_i(\boldsymbol{v}) \\
> &= \left(\sum_{i=1}^{n}  a_i \boldsymbol{\widetilde{\sigma}}_i\right) (\boldsymbol{v})
>\end{align}$$
> Since $\boldsymbol{v}$ is arbitrary and $a_i$ is mapped from the basis of the vector space $V$, one can express any dual space element by the given basis.
> $$\tag*{$\square$}$$

>[!remark] Remark
> The elements of the dual space, i.e. linear functionals, are also called **forms**.

>[!def] Definition $p$-forms
> Let $V^*$ denote the dual of vector space $V$ with $\dim(v) = n$. The vector space $\bigwedge^p V^*$ is a vector space of $p$-forms.

>[!example] Examples
> 1. $\bigwedge^0 V^*$ is the space of **scalar-valued functionals**, i.e. 
> $$\boldsymbol{\widetilde{\alpha}}: \bigwedge^0 V \to \mathbb{K}$$
> an example would be
> $$\begin{align}
> &\boldsymbol{\widetilde{\alpha}}: \mathbb{R} \to \mathbb{R}\\
> &\boldsymbol{\widetilde{\alpha}}(x) = 2x 
>\end{align}$$
> $0$-Forms act on the underlying field of the vector space, i.e. the scalars.
> 2. $\bigwedge^1 V^*$ is the space of **vector valued functionals**, i.e.
> $$\boldsymbol{\widetilde{\alpha}}: \bigwedge^1 V \to \mathbb{K}$$
> Let $\boldsymbol{v} \in \bigwedge^1 \mathbb{R}^3$. An example would be
> $$\begin{align}
> &\boldsymbol{\widetilde{\alpha}}: \bigwedge^1 \mathbb{R}^3 \to \mathbb{R} \\
> &\boldsymbol{\widetilde{\alpha}}(\boldsymbol{v}) = 2v^1 + 4v^2 -3v^3
>\end{align}$$
> $1$-forms act on the vector field itself, which geometrically are considered lines in the vector field.
> 3. $\bigwedge^2 V^*$ is the space of **$2$-vector functionals**, i.e.
> $$\boldsymbol{\widetilde{\alpha}}: \bigwedge^2 V \to \mathbb{K}$$
> Let $\boldsymbol{v} \wedge \boldsymbol{u} \in \bigwedge^2 \mathbb{R}^2$. An example would be
> $$\begin{align}
> &\boldsymbol{\widetilde{\alpha}}: \bigwedge^2 \mathbb{R}^2\\
> &\boldsymbol{\widetilde{\alpha}}(\boldsymbol{v} \wedge \boldsymbol{u}) = v^1u^2 - v^2u^1
>\end{align}$$
> which computes the area of the spanned area. $2$-forms act on the vector field of faces spanned by the vectors of the underlying vector fields. They evaluate the faces according to the functional.

>[!remark] Final Remark on this Section
> This concept of exterior algebra holds true as introduced for vector spaces. To generalize this concept we need to concept of **manifolds, tangent spaces and cotangent spaces**.

### Manifolds, Tangent Spaces and Cotangent Spaces

Basic concepts are introduced. For now it is sufficient to understand that a **(sub)manifold**  is a subset $\mathcal{M} = \mathcal{M}^n \subseteq \mathbb{R}^{n+r}$ which behaves locally Euclidean. When speaking about manifolds we do not require them to be globally non-Euclidean, though those are of particular interest. The manifold can be described by $n$ coordinates in itself, while globally it can also be described by $n+r$ coordinates. The manifold itself does not necessarily need to be equipped by a global coordinate system.

Denote $q \in \mathcal{M}$ a point on a manifold, we define the **tangent space** to the manifold $\mathcal{M}$ at point $q$ as $T \mathcal{M}_q^n$ as the real vector space.

>[!remark] Summary
> - Manifold is $\mathcal{M} = \mathcal{M}^n \subseteq \mathbb{R}^{n+r}$
>   - if $r \geq 1$ we call $\mathcal{M}$ a **submanifold**
>   - often the manifold is highlighted to be of dimension $n$ by writing $\mathcal{M}^n$
> - Tangent Space to $\mathcal{M}$ at point $q \in \mathcal{M}$ is $T_{q} \mathcal{M}$
>   - vector space consisting of all tangent vectors to $q$
> - Tangent Bundle $T\mathcal{M}$ consisting of all tangent spaces over all points.
>   - $T \mathcal{M} = \{ T_{q} \mathcal{M} \,|\, q \in \mathcal{M}\}$

---
>[!remark] Motivation: Tangent Vector Operators

First we highlight how we think about the directional derivative. For the upcoming text we denote
- $q \in \mathcal{M}$ a point on the manifold
- $\boldsymbol{v} \in T_q \mathcal{M}^n$ a tangent vector
- $f: \mathcal{M}^n \to \mathbb{R}$ a differentiable function

For illustrative purposes we imagine some physical setting. Consider a **force** acting on **point** $q$ in **direction** $\boldsymbol{v}$ evolving over some time $t$
$$\left(D_{\boldsymbol{v}} f \right) (q) \equiv \frac{\text{d}}{\text{d}t}\Big[ f(q+t \boldsymbol{v}) \Big]_{t=0}$$
Note, $f$ could for instance express what force/acceleration the directional vector causes on point $q$ over time $t$. Hence, the directional derivative tells us what the rate of change in direction $\boldsymbol{v}$ is evaluated at point $q$.

In vector calculus we define the directional derivative as follows 

>[!def] Definition Directional Derivative
> The **directional derivative** of $f: \mathbb{R}^n \to \mathbb{R}$ in the direction of the unit vector $\boldsymbol{v} \in \mathbb{R}^n$ is 
>$$D_{\boldsymbol{v}} f(\boldsymbol{x}) = \lim_{t \to 0} \frac{f(\boldsymbol{q} + t\boldsymbol{v}) - f(\boldsymbol{q})}{t}$$
> if this limit exists.

where the notion of $\boldsymbol{v}$ being a unit vector tells us that $\left\vert\left\vert\, \boldsymbol{v} \,\right\vert\right\vert = \sqrt{\sum_{i=1}^{n} {(v^i)}^2}= 1$. That $\boldsymbol{v}$ is a unit vector is not necessarily required, but makes interpretation of the derivate easier. Now, observe that $\boldsymbol{v}$ can be decomposed over its canonical base vectors $\boldsymbol{e}_{i}$. Therefore 
$$\boldsymbol{v} = \sum_{i=1}^{n}v^i\boldsymbol{e}_{i}$$
Note, that if we take the directional derivative with respect to $\boldsymbol{e}_{i}$ we get the partial derivative
$$D_{\boldsymbol{e}^{i}} f = \frac{\partial f}{\partial x^i}$$
Now, since we can decompose $\boldsymbol{v}$ we can also decompose the directional derivative in its partial derivatives and have
$$D_{\boldsymbol{v}} f = \sum_{i=1}^{n} \underbrace{\frac{\partial f}{\partial x^i}}_{\sim \boldsymbol{e}_{i}} v^i$$
This can be summarized in the following theorem
>[!theorem] Theorem Directional Derivative Adaptation 
> If $f: \mathbb{R}^n \to \mathbb{R}$ is a differentiable function for all $\boldsymbol{x}_i$ with $1 \leq i \leq n$, then $f$ has directional derivatives in the direction of unit vector $\boldsymbol{v} \in \mathbb{R}^n$ and
> $$D_{\boldsymbol{v}} f(\boldsymbol{x}) = \sum_{i=1}^n \frac{\partial f(\boldsymbol{x})}{\partial x^i} \cdot v^i$$
>>[!proof]-
>> Define $$g(h) = f(\boldsymbol{x} + h\boldsymbol{v})$$Taking the derivative of $g$ with respect to $h$ using the definition 
>> $$\begin{align}
>> \frac{d g}{dh} &= \lim_{t \to 0} \frac{g(h + t) - g(h)}{t} \\
>> &= \lim_{t \to 0} \frac{f(\boldsymbol{x} + (h+t)\boldsymbol{v})- f(\boldsymbol{x} + h\boldsymbol{v})}{t}\tag{1}
>>\end{align}$$
>> Applying the chain rule to compute $\frac{d g}{d h}$ gives
>> $$ \frac{d g}{d h} = \sum_{i=1}^n \frac{\partial f}{\partial x^i}\frac{d x^i}{d h}$$
>> Note that $x^i \mapsto x^i + h v^i$ for the $i$-th component of $\boldsymbol{x}$, thus $\frac{d x^i}{d_h} = v^i$, therefore
>> $$\frac{d g}{d h} = \sum_{i=1}^n \frac{\partial f}{\partial x^i} v^i \tag{2}$$
>> Now combining $(1)$ and $(2)$ gives 
>> $$\lim_{t \to 0} \frac{f(\boldsymbol{x} + (h+t)\boldsymbol{v})- f(\boldsymbol{x} + h\boldsymbol{v})}{t}= \sum_{i=1}^n \frac{\partial f(\boldsymbol{x})}{\partial x^i} v^i$$
>> Evaluating $g$ at $h=0$ yields 
>> $$\lim_{t \to 0} \frac{f(\boldsymbol{x} + t\boldsymbol{v})- f(\boldsymbol{x})}{t} = \sum_{i=1}^n \frac{\partial f(\boldsymbol{x})}{\partial x^i} v^i$$
>> which proves the theorem.
>> $$\tag*{$\square$}$$

Note, that by rewriting the directional derivative as presented, we can interpret the directional derivative as the sum of all partial derivatives scaled by the directional vector $\boldsymbol{v}$. Now, we can rewrite $\boldsymbol{v}: C \to \mathbb{R}$ to be an operator defined over the coefficients $v^i$, i.e.
$$\boldsymbol{v}\left.\vphantom{_{q}}\right\vert_{q} = \sum_{i=1}^{n}v^i \left.\vphantom{q}\frac{\partial}{\partial x^i} \right\vert_{q}$$
In this text and the book $\boldsymbol{v}$ is used as a vector and operator. Since the operator $\boldsymbol{v}$ itself is represented as a vector over $\boldsymbol{v} \in T_q \mathcal{M}$, we can consider the operator itself also as a vector over a vector space of differential operators. The basis can easily be identified by
$$\frac{\boldsymbol{\partial}}{\boldsymbol{\partial}x^j} = D_{\boldsymbol{e}^{j}}$$
Hence, any differential operator can be decomposed over its basis as
$$\boldsymbol{v} = \sum_{i=1}^{n}v^j \frac{\boldsymbol{\partial}}{\boldsymbol{\partial}x^j}$$

>[!remark] Summary
> - the tangent vector $\boldsymbol{v}$ acts as differential operator on scalar function
>   - $\boldsymbol{v} = \sum_{i=1}^{n} v^i \left.\vphantom{q}\frac{\boldsymbol{\partial}}{\boldsymbol{\partial}x^i}\right\vert_{q}$
> - $\left\{\frac{\boldsymbol{\partial}}{\boldsymbol{\partial}x_i}\right\}_{i=1}^n$ form a basis for the tangent space $T_q \mathcal{M}^n$
