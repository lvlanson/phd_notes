---
aliases:
- multivariate calculus
---
>[!terminology]
>
| Term                                            | Meaning                                                                            |
| ----------------------------------------------- | ---------------------------------------------------------------------------------- |
| Real Valued Function $f$                        | $f:\mathbb{R} \rightarrow \mathbb{R}$                                              |
| Scalar Valued Function $f$ <br>or Sacalar Field | $f:\mathbb{R} \rightarrow \mathbb{R}^m$ with $m>1$                                 |
| Vector Valued Function $f$ <br>or Vector Field  | $\mathbf{f}:\mathbb{R}^n \rightarrow \mathbb{R}^m$ with $m,n > 1$                  |
| Components                                      | If $\mathbf{f}$ is a vector field, then $f_i \in \mathbf{f}$ is called a component | 

>[!def] Definition Open Ball ([[../../../Sources/apostol1967.pdf#page=269|Source]])
>Let $\mathbf{a} \in \mathbb{R}^n$ with $r>0$. The set $\mathbf{x} \in\mathbb{R}^n$ satisfying
>$$ \lvert\lvert \mathbf{x} -\mathbf{a} \rvert\rvert < r$$
>is called the **open $n$-ball**. We denote it
>$$ B(\mathbf{a}, r) = \{ \mathbf{x} \in \mathbb{R}^n \; \vert \; \lvert\lvert \mathbf{x} - \mathbf{a} \rvert\rvert < r \}$$

>[!def] Definition Interior Point ([[../../../Sources/apostol1967.pdf#page=269|Source]])
> Let $S \subset \mathbb{R}^n$ and assume $\mathbf{a} \in S$. The point $\mathbf{a}$ is called an interior point of $S$ if there exists some $r > 0$ with $$ B(\mathbf{a}, r) \subseteq S$$
> The set of all interior points with respect to $S$ is denoted as
> $$ \text{int } S$$

>[!def] Definition Open Set ([[../../../Sources/apostol1967.pdf#page=269|Source]])
>A set $S$ in $\mathbb{R}^n$ is called open if all its points are interior points, i.e. 
>$$ S \text{ is open } \Leftrightarrow S = \text{int } S$$

>[!def] Definition Exterior Point ([[../../../Sources/apostol1967.pdf#page=270|Source]])
>A point $\mathbf{a} \in \mathbb{R}^n$ is said to be **exterior** with respect to a set $S \in \mathbb{R}^n$ if 
>$$\exists r > 0 \; : \; B(\mathbf{a}, r) \cap S = \emptyset$$
>The set of all exterior points with respect to $S$ is denoted as
>$$ \text{ext } S$$

>[!def] Definition Boundary Point ([[../../../Sources/apostol1967.pdf#page=270|Source]])
>A point $\mathbf{a} \in \mathbb{R}^n$ is said to be a **boundary point** of $S$ if it's neither an interior nor exterior point of $S$. The set of all boundary points of $S$ is denoted as $$ \partial S$$

>[!def] Definition Derivative of a Scalar Field with Respect to a Vector ([[../../../Sources/apostol1967.pdf#page=278|Source]])
> Let 
> - $f: S \rightarrow \mathbb{R}^n$  be a scalar field with $S \subseteq \mathbb{R}^n$
> - $\mathbf{a} \in S$ interior point of $S$
> - $\mathbf{y} \in \mathbb{R}^n$ an arbitrary point
> - $h \in \mathbb{R}$ with $h \neq 0$
>
>The derivative of $f$ at $\mathbf{a}$ with respect to $\mathbf{y}$ is denoted by
>$$f'(\mathbf{a}; \mathbf{y}) = \lim_{ h \to 0 } \frac{f(\mathbf{a + h\mathbf{y}}) - f(\mathbf{a})}{h}$$
>when the limit on the right exists.
>>[!remark]
>>1. the quotient is called the **average rate of change** of $f$ over the line segment joining $\mathbf{a}$ to $\mathbf{a} + h\mathbf{y}$ 
>>2. as $h$ decreases the line segment joins
>>3. since $\mathbf{a}$ is an interior point, i.e. $\exists r \in \mathbb{R}\,:\; B(\mathbf{a}, r) \in S$ then the line segment $\mathbf{a} + h\mathbf{y}$ will also lie in $S$ if $h$ is chosen such that $\lvert h \rvert \lvert\lvert y \rvert\rvert< r$
>>4. If $\mathbf{y} = \mathbf{0}$ the difference is $0$ and therefore the limit is $0$, hence $f(\mathbf{a}, 0)$ always exists.

>[!theorem] Theorem ([[../../../Sources/apostol1967.pdf#page=278|Source]])
>Let $g(t) = f(\mathbf{a}+ t\mathbf{y})$. If one of the derivatives exists, then the other also exists, and they are equal, i.e.
>$$g'(t) = f'(\mathbf{a} + t\mathbf{y}; \mathbf{y})$$
>In particular, when $t=0$ we have $g'(0) =f'(\mathbf{a}; \mathbf{y})$.
>>[!proof]
>>We determine the difference quotient such that
>>$$\begin{align}
>> \lim_{ h \to 0 } \frac{g(t+h)-g(t)}{h} &= \lim_{ h \to 0 }\frac{f(\mathbf{a}+t\mathbf{y}+h\mathbf{y})-f(\mathbf{a},t\mathbf{y})}{h} \\ \\
>> g'(t) &= f'(\mathbf{a}+ t\mathbf{y}; \mathbf{y}) \tag{By Definition}  \\
>> \,\tag*{$\square$}
>>\end{align}$$

>[!theorem] Mean Value Theorem for Derivatives of Scalar Fields ([[../../../Sources/apostol1967.pdf#page=279|Source]])
>Assume $f'(\mathbf{a}+ t\mathbf{y}; \mathbf{y})$ exists with $0 \geq t \geq 1$. Then for some real number $0 < \Theta < 1$ we have
>$$f(\mathbf{a}+ \mathbf{y})-f(\mathbf{a}) = f'(\mathbf{z}; \mathbf{y}), \qquad \text{with } \mathbf{z} = \mathbf{a} + \Theta \mathbf{y}$$