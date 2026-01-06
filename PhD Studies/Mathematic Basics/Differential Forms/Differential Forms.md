---
id: Differential Forms
aliases: []
tags: []
---
## 2.1 Coordinate Functions

We will denote **elements of a manifold** as points and represent them as $n$-tuples
- $(x_{1},x_{2},\dots,x_{n}) \in \mathbb{R}^n$

and **elements of a vector space** as column vectors
- $\begin{bmatrix} x_{1}, x_{2}, \dots, x_{n}\end{bmatrix}^T \in \mathbb{R}^n$

>[!def] Definition Dual Space of a Vector Space
> Let $V$ be a vector space, then the dual space $V^*$ of $V$ is the set of all linear functionals on $V$.

It is convention to use superscripts instead of using subscripts for linear functionals of the dual space $V^*$. Let $\boldsymbol{e}_i$ be a unit vector of $V$ with the $i$-th entry being $1$ and else $0$. Then the corresponding functional $T_1 \in V^*$ is also written as a vector $\boldsymbol{e}^1 \in V^*$, such that 
$$\begin{align}
\boldsymbol{e}^1(\boldsymbol{e}_1) &= \delta_{11} = 1  \\
\boldsymbol{e}^1(\boldsymbol{e}_2) &= \delta_{12} = 0
\end{align}$$
where $\delta_{ij} = \begin{cases} 1 & \text{ if } i = j \\ 0 & \text{ else } \end{cases}$. Hence, 
$$T_i = \boldsymbol{e}^i(\boldsymbol{e}_j) = \delta_{ij}$$

>[!lemma] Lemma 
> The set $\{\boldsymbol{e}^1, \ldots, \boldsymbol{e}^n\} \subset V^*$ induced by the basis vectors $\boldsymbol{e}_i \in V$ form a basis of $V^*$.

>[!proof]-
> **Linear Indendence**
> Let $\boldsymbol{e}^i$ be the linear functional mapping $\boldsymbol{e}^i(\boldsymbol{e}_j) = \delta_{ij}$. Then we have by the requirement of a basis beinag linearly independent, that
> $$ \sum_{i=1}^n c_i \boldsymbol{e}^i = \boldsymbol{0}_{V^*}$$
> with $c_i = 0$ being the only solution. Note, on the right hand side $\boldsymbol{0} \in V^*$ is a linear functional mapping to $0 \in \mathbb{K}$. Further, denote $\boldsymbol{e}_j \in V$ some arbitrary basis vector of $V$. Then by definition
> $$ \sum_{i=1}^n c_i\boldsymbol{e}^i(\boldsymbol{e}_j) = 0$$
> Since $\boldsymbol{e}^i(\boldsymbol{e}_j) = \delta_{ij}$, we have 
> $$ c_j = 0 $$
> for all $1 \leq j \leq n$, which confirms all $\boldsymbol{e}^j$ are linearly independent.
> 
> **Spanning of $V^*$**
> Let $\boldsymbol{f} \in V^*$ be an arbitrary linear functional. By definition of basis vectors, it is to show that it holds that
> $$ \sum_{i=1}^n \lambda_i\boldsymbol{e}^i = \boldsymbol{f}$$
> with $\lambda_i \in \mathbb{K}$. Now, denote $\boldsymbol{v} \in V$. Since $\boldsymbol{f}$ is a linear functional of $V$ we can write 
> $$\begin{align} 
>   \boldsymbol{f}\left( \boldsymbol{v} \right) &= \boldsymbol{f}\left(\sum_{i=1}^n \lambda_i\boldsymbol{e}^i\right) \\
> &= \sum_{i=1}^n \lambda_i \boldsymbol{f}(\boldsymbol{e}^i) \tag{Linearity}
>\end{align}$$
> Notice, $\boldsymbol{e}^i(\boldsymbol{v}) = \lambda_i$. Therefore, we can write
> $$ \begin{align}\boldsymbol{f}(\boldsymbol{v}) = \sum_{i=1}^n \lambda_i \boldsymbol{f}(\boldsymbol{e}^i) &= \sum_{i=1}^n \boldsymbol{e}^i(\boldsymbol{v})\boldsymbol{f}(\boldsymbol{e}^i) \\
> &= \left(\sum_{i=1}^n \boldsymbol{e}^i \boldsymbol{f}(\boldsymbol{e}^i)\right)(\boldsymbol{v})
>\end{align}$$
> Hence, any linear functional $\boldsymbol{f}$ can represented as 
> $$ \boldsymbol{f} = \sum_{i=1}^n \boldsymbol{e}^i \boldsymbol{f}(\boldsymbol{e}^i)$$
> which therefore spans the dual space $V^*$.
> $$ \tag*{$\square$}$$


We will further make the destinction between **functions and functionals**
- **functions** map from a manifold
$$ f: \mathbb{R}^n \to \mathbb{R}$$
- **functionals** map from a vector space
$$ f: \mathbb{R}^n \to \mathbb{R}$$

>[!def] Definition Coordinate Function
> Let $\boldsymbol{x}_i: M \to \mathbb{K}$ denote a linear functional on the manifold $M$. Let $\boldsymbol{p} \in M$ denote a point. We call $\boldsymbol{x}_i$ a **coordinate function** if
>$$\boldsymbol{x}_i(\boldsymbol{p}) = p_i$$
> i.e. $\boldsymbol{x}_i$ extracts the $i$-th coordinate from any point in $M$.

For convenience if we are in $\mathbb{R}^2$ or $\mathbb{R}^3$ we will write $\boldsymbol{x},\boldsymbol{y},\boldsymbol{z}$ as the representative coordinate functions.

## 2.2 Tangent Spaces

Intuitively, 
- a **manifold** is a space that is **locally Euclidean**. Conceptionally speaking, if we zoom in far enough into some area of our manifold, it would more and more look like the Euclidean space we are used to working on, but zooming out we could observe any space such as a **torus** or a **hypersphere**.
- a **tangent space** is the space which is tangent to a point $\boldsymbol{p}$ from a manifold.

>[!remark] Remark on Manifolds and Vector Spaces
> It is true, that for $\mathbb{R}^n$ the vector space axioms hold, hence $\mathbb{R}^n$ is a vector space. Since, all the elements of $\mathbb{R}^n$ can also be thought of points, i.e. $n$-tuples, it can also be understood as a manifold.
>
> However, a torus or sphere can't be thought of a vector space, since it does not naturally hold the vector axioms. This can be easily understood since an element of a torus can be scaled outside of the torus. The same is true for adding arbitrary elements of the torus, thus violating the vector space axioms. While the manifold itself isn't a vector space, each point p on the manifold has an associated vector space $T_pM$. We use these 'local' vector spaces to perform calculus on the 'non-linear' manifold.

>[!def] Definition Tangent Space 
> Let $M$ denote a manifold and let $\boldsymbol{p} \in M$. We call $T_p M$ or $T_p(M)$ the **tangent space** to manifold $M$ at point $\boldsymbol{p}$.

>[!remark] Remark 
> All vectors of $T_pM$ are tangent to $p$.

>[!def] Definition Tangent Bundle 
> Let $T_pM$ denote a tangent space to manifold $M$ at point $\boldsymbol{p}$. The manifold $M$ bundled with tangent spaces at every point $\boldsymbol{p} \in M$ is called the **tangent bundle** $TM$ or $T(M)$.

>[!remark] Remark
> Let the dimension of $M$ be $n$. Then the dimension of $TM$ is $2n$. For each point $\boldsymbol{p}\in M$ a separate vector field can be defined as a tangent space. Since both spaces have dimensionality $n$ must have dimensionality $2n$.

## 2.3 Directional Derivatives

We first look at directional derivatives from a multivariable calculus angle. Therefore we look at the **directional derivative as a vector on the manifold**.

>[!def] Definition Directional Derivative
> The **directional derivative** of $f: \mathbb{R}^n \to \mathbb{R}$ in the direction of the unit vector $\boldsymbol{u} \in \mathbb{R}^n$ is 
>$$D_{\boldsymbol{u}} f(\boldsymbol{x}) = \lim_{t \to 0} \frac{f(\boldsymbol{x} + t\boldsymbol{u}) - f(\boldsymbol{x})}{t}$$
> if this limit exists.

This is the classical multivariate calculus version of the directional derivative. We will put some work to rewrite it in a more general way, such that it is more fitting for the work on tangent spaces.

>[!remark] Remark
> The notation $D_{\boldsymbol{u}}$ highlights to take the directional derivative with respect to a unit vector $\boldsymbol{u}$. Given the one dimensional case, we'd just take $D_{1} = d$.

>[!remark]
> Alternatively for $\boldsymbol{p} \in \mathbb{R}^n$ one can write 
> $$\lim_{t\to 0} \frac{f(\boldsymbol{p}+t\boldsymbol{u}) - f(\boldsymbol{p})}{t} = \frac{d}{dt} \left.\left(f(\boldsymbol{p}+t\boldsymbol{u}) \vphantom{\frac{d}{dt}}\right)\right|_{t=0}$$

>[!remark]
> If $\boldsymbol{u} = \boldsymbol{e}_i$, then
> $$D_{\boldsymbol{u}}f = D_{\boldsymbol{e}_i} f = \frac{\partial f}{\partial x_i}$$

>[!theorem] Theorem Directional Derivative Adaptation 
> If $f: \mathbb{R}^n \to \mathbb{R}$ is a differentiable function for all $\boldsymbol{x}_i$ with $1 \leq i \leq n$, then $f$ has directional derivatives in the direction of any unit vector $\boldsymbol{u} \in \mathbb{R}^n$ and
> $$D_{\boldsymbol{u}} f(\boldsymbol{x}) = \sum_{i=1}^n \frac{\partial f(\boldsymbol{x})}{\partial x_i} \cdot u_i$$

>[!proof]
> Define $$g(h) = f(\boldsymbol{x} + h\boldsymbol{u})$$Taking the derivative of $g$ with respect to $h$ using the definition 
> $$\begin{align}
> \frac{d g}{dh} &= \lim_{t \to 0} \frac{g(h + t) - g(h)}{t} \\
> &= \lim_{t \to 0} \frac{f(\boldsymbol{x} + (h+t)\boldsymbol{u})- f(\boldsymbol{x} + h\boldsymbol{u})}{t}\tag{1}
>\end{align}$$
> Applying the chain rule to compute $\frac{d g}{d h}$ gives
> $$ \frac{d g}{d h} = \sum_{i=1}^n \frac{\partial f}{\partial x_i}\frac{d x_i}{d h}$$
> Note that $x_i \mapsto x_i + h u_i$ for the $i$-th component of $\boldsymbol{x}$, thus $\frac{d x_i}{d_h} = u_i$, therefore
> $$\frac{d g}{d h} = \sum_{i=1}^n \frac{\partial f}{\partial x_i} u_i \tag{2}$$
> Now combining $(1)$ and $(2)$ gives 
> $$\lim_{t \to 0} \frac{f(\boldsymbol{x} + (h+t)\boldsymbol{u})- f(\boldsymbol{x} + h\boldsymbol{u})}{t}= \sum_{i=1}^n \frac{\partial f(\boldsymbol{x})}{\partial x_i} u_i$$
> Evaluating $g$ at $h=0$ yields 
> $$\lim_{t \to 0} \frac{f(\boldsymbol{x} + t\boldsymbol{u})- f(\boldsymbol{x})}{t} = \sum_{i=1}^n \frac{\partial f(\boldsymbol{x})}{\partial x_i} u_i$$
> which proves the theorem.
> $$\tag*{$\square$}$$

>[!remark] Remark on the Requirement of Unit Vectors
> Note, we required $\boldsymbol{u}$ being a unit vector in $D_{\boldsymbol{u}}$. Note, when computing the slope of a tangent, we compute $$\frac{\text{rise}}{\text{length}}$$  
> Let $T$ denote the tangent plane to some function $f$. We represent the **rise** by the vector $\boldsymbol{u}$ and the **length** of it by its norm $\left\vert\left\vert\,\boldsymbol{u}\,\right\vert\right\vert$. To compute the rise at some point $\boldsymbol{p}\in M$, we take the difference between the point $x_{i} + u_{i}$ and $x_{i}$. Since the tangent space is a **vector space**, we can shift the vectors in the tangent space as we wish. So the slope of tangent space can be described as
> $$ \frac{\sum_{i=1}^{n}T(p_i + u_i) - T(p_i)}{\left\vert\left\vert\, \boldsymbol{u} \,\right\vert\right\vert}$$
> Since we chose to describe the tangent $T$ with respect to the point $\boldsymbol{p}$ on the manifold described by the function $f$, we can also describe the slope by the directional derivatives scaled by the unit vector $\boldsymbol{u}$, i.e. 
> $$ \frac{\sum_{i=1}^{n}\frac{\partial f}{\partial x_i} \left.\vphantom{\dfrac{a}{b}}\right\vert_{\boldsymbol{p}} u_i}{\left\vert\left\vert\, \boldsymbol{u} \,\right\vert\right\vert} = \frac{\sum_{i=1}^{n}\frac{\partial f}{\partial x_i} u_i}{\left\vert\left\vert\, \boldsymbol{u} \,\right\vert\right\vert} $$
> Since $\boldsymbol{u}$ is a unit vector, i.e. $\left\vert\left\vert\, \boldsymbol{u} \,\right\vert\right\vert = 1$ it follows thatwe yield the expression from our last theorem, i.e.
> $$ D_{\boldsymbol{u}}f = \sum_{i=1}^{n}\frac{\partial f}{\partial x_i} u_i $$
> **The takeaway is, that the calculus definition of the directional derivative is the same as the derived formula from the theorem, as long as $\left\vert\left\vert\, \boldsymbol{u} \,\right\vert\right\vert = 1$.**

We will now loosen the restriction of $\boldsymbol{u}$ being a unit vector, which enables us to freely describe the tangent space. It is important to note, that we do not describe the slop of the tangent anymore. The next definition will describe how to describe a tangent space with respect to a point $\boldsymbol{p} \in M$

>[!def] Definition Directional Derivative
> Let $f: \mathbb{R}^n \to \mathbb{R}$ be a real-valued function on the manifold $\mathbb{R}^n$ and let $\boldsymbol{v}_{p}$ be a vector tangent to the manifold $\mathbb{R}^n$ at point $\boldsymbol{p}\in \mathbb{R}^n$, i.e. $\boldsymbol{v}_{\boldsymbol{p}} \in T_{p}(\mathbb{R}^n)$. The number
> $$ \boldsymbol{v}_{\boldsymbol{p}}[f] \equiv \frac{d}{dt} \left(\vphantom{\frac{a}{b}} f(\boldsymbol{p} + t \boldsymbol{v}_{\boldsymbol{p}})\right) \left.\vphantom{\dfrac{a}{b}}\right\vert_{t=0} $$

>[!remark] Remark on the Mathematical Object $\boldsymbol{v_p}$
> Note, $\boldsymbol{v_p}$ takes a function as input. We call $\boldsymbol{v_p}$ an **operator**. 
