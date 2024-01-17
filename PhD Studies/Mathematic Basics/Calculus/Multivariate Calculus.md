---
aliases:
- multivariate calculus
---
>[!terminology]
>
>| Term                                            | Meaning                                            |
>| ----------------------------------------------- | -------------------------------------------------- |
>| Real Valued Function $f$                        | $f:\mathbb{R} \rightarrow \mathbb{R}$              |
>| Scalar Valued Function $f$ <br>or Sacalar Field | $f:\mathbb{R} \rightarrow \mathbb{R}^m$ with $m>1$ |
>| Vector Valued Function $f$ <br>or Vector Field  | $\mathbf{f}:\mathbb{R}^n \rightarrow \mathbb{R}^m$ with $m,n > 1$                                                   |

>[!def] Definition Open Ball ([[../../../Sources/apostol1967.pdf#page=266|Source]])
>Let $\mathbf{a} \in \mathbb{R}^n$ with $r>0$. The set $\mathbf{x} \in\mathbb{R}^n$ satisfying
>$$ \lvert\lvert \mathbf{x} -\mathbf{a} \rvert\rvert < r$$
>is called the **open $n$-ball**. We denote it
>$$ B(\mathbf{a}, r) = \{ \mathbf{x} \in \mathbb{R}^n \; \vert \; \lvert\lvert \mathbf{x} - \mathbf{a} \rvert\rvert < r \}$$

>[!def] Definition Interior Point ([[../../../Sources/apostol1967.pdf#page=266|Source]])
> Let $S \subset \mathbb{R}^n$ and assume $\mathbf{a} \in S$. The point $\mathbf{a}$ is called an interior point of $S$ if there exists some $r > 0$ with $$ B(\mathbf{a}, r) \subseteq S$$
> The set of all interior points with respect to $S$ is denoted as
> $$ \text{int } S$$

>[!def] Definition Open Set ([[../../../Sources/apostol1967.pdf#page=266|Source]])
>A set $S$ in $\mathbb{R}^n$ is called open if all its points are interior points, i.e. 
>$$ S \text{ is open } \Leftrightarrow S = \text{int } S$$

>[!def] Definition Exterior Point ([[../../../Sources/apostol1967.pdf#page=267|Source]])
>A point $\mathbf{a} \in \mathbb{R}^n$ is said to be **exterior** with respect to a set $S \in \mathbb{R}^n$ if 
>$$\exists r > 0 \; : \; B(\mathbf{a}, r) \cap S = \emptyset$$
>The set of all exterior points with respect to $S$ is denoted as
>$$ \text{ext } S$$

>[!def] Definition Boundary Point ([[../../../Sources/apostol1967.pdf#page=267|Source]])
>A point $\mathbf{a} \in \mathbb{R}^n$ is said to be a **boundary point** of $S$ if it's neither an interior nor exterior point of $S$. The set of all boundary points of $S$ is denoted as $$ \partial S$$