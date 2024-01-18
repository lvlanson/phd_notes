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
>$$f'(\mathbf{a}; \mathbf{y}) = \lim_{ h \to 0 } \frac{f(\mathbf{a} + h\mathbf{y}) - f(\mathbf{a})}{h}$$
>when the limit on the right exists.
>>[!remark]
>>1. the quotient is called the **average rate of change** of $f$ over the line segment joining $\mathbf{a}$ to $\mathbf{a} + h\mathbf{y}$ 
>>2. as $h$ decreases the line segment joins
>>3. since $\mathbf{a}$ is an interior point, i.e. $\exists r \in \mathbb{R}\,:\; B(\mathbf{a}, r) \in S$ then the line segment $\mathbf{a} + h\mathbf{y}$ will also lie in $S$ if $h$ is chosen such that $\lvert h \rvert \lvert\lvert y \rvert\rvert< r$
>>4. If $\mathbf{y} = \mathbf{0}$ the difference is $0$ and therefore the limit is $0$, hence $f(\mathbf{a}, 0)$ always exists.

^c18601

>[!theorem] Theorem ([[../../../Sources/apostol1967.pdf#page=278|Source]])
>Let $g(t) = f(\mathbf{a}+ t\mathbf{y})$. If one of the derivatives exists, then the other also exists, and they are equal, i.e.
>$$g'(t) = f'(\mathbf{a} + t\mathbf{y}; \mathbf{y})$$
>In particular, when $t=0$ we have $g'(0) =f'(\mathbf{a}; \mathbf{y})$.
>>[!proof]-
>>We determine the difference quotient such that
>>$$\begin{align}
>> \lim_{ h \to 0 } \frac{g(t+h)-g(t)}{h} &= \lim_{ h \to 0 }\frac{f(\mathbf{a}+t\mathbf{y}+h\mathbf{y})-f(\mathbf{a},t\mathbf{y})}{h} \\ \\
>> g'(t) &= f'(\mathbf{a}+ t\mathbf{y}; \mathbf{y}) \tag{By Definition}  \\
>> \,\tag*{$\square$}
>>\end{align}$$

>[!theorem] Mean Value Theorem for Derivatives of Scalar Fields ([[../../../Sources/apostol1967.pdf#page=279|Source]])
>Assume $f'(\mathbf{a}+ t\mathbf{y}; \mathbf{y})$ exists with $t \in[0,1]$. Then for some real number $\Theta \in (0,1)$ we have
>$$f(\mathbf{a}+ \mathbf{y})-f(\mathbf{a}) = f'(\mathbf{z}; \mathbf{y}), \qquad \text{with } \mathbf{z} = \mathbf{a} + \Theta \mathbf{y}$$
>>[!proof]-
>>We will use the same ideas as in the [[Differentiation#^71d429|real valued mean value theorem]]. We denote the real value function 
>>$$ g(t) = f(\mathbf{a}+t\mathbf{y})$$
>>We apply the [[Differentiation#^71d429|mean value theorem]] on $g$ over the interval $[0,1]$, such that we have for $\Theta \in (0,1)$
>>$$\begin{align}
>> g'(\Theta)= g(1)- g(0) \tag{1}
>>\end{align}$$
>>Note, the mappings
>>$$\begin{align}
>> g(1) &= f(\mathbf{a} + \mathbf{y}) \\
>> g(0) &= f(\mathbf{a}) \\
>> g(1)- g(0) &= f(\mathbf{a}+\mathbf{y})- f(\mathbf{a}) \tag{2}
>>\end{align}$$
>>Hence, $(1)$ and $(2)$ conclude
>>$$\begin{align}
>> g'(\Theta) &= f(\mathbf{a}+\mathbf{y})- f(\mathbf{a}) \tag*{$\square$}
>>\end{align}$$
>
>>[!note]-
>>Usually instead of $\mathbf{a}+\mathbf{y}$ the variable $\mathbf{b}$ is used, as it can also be seen in the [[Differentiation#^71d429|real valued mean value theorem]].

>[!def] Definition Directional Derivative ([[../../../Sources/apostol1967.pdf#page=279|Source]])
>If $\mathbf{y} \in \mathbb{R}^n$ is a normed vector, i.e. $\lvert\lvert y \rvert\rvert = 1$ The derivative $f'(\mathbf{a}; \mathbf{y})$ is called **the directional derivative of $f$ at $\mathbf{a}$ in the direction of $\mathbf{y}$**.

^c59e8c

>[!def] Definition Partial Derivative ([[../../../Sources/apostol1967.pdf#page=279|Source]])
> The partial derivative is a particular form of the [[Multivariate Calculus#^c59e8c | directional derivative]], with $\mathbf{y} \in \mathbb{R}^n$ being the unit vector $\mathbf{e}_{k}$. Therefore, the partial derivative with respect to $\mathbf{e}_{k}$can be given as
> $$D_{k}f(\mathbf{a})=f'(\mathbf{a}; \mathbf{e}_{k})$$
> The following notations can also be used for the partial derivative $D_kf(\mathbf{a})$:
> $$\begin{align}
> D_{k}f&(a_{1}, \ldots, a_{n}) \\ \\
> \frac{\partial f}{\partial x_{k}}&(a_{1}, \dots, a_{n})\\ \\
> f'_{x_{k}}&(a_{1}, \dots, a_{n})
>\end{align}$$

>[!def] Definition Higher Order Partial Derivatives ([[../../../Sources/apostol1967.pdf#page=280|Source]])
> Given some scalar field $D_{1}f, \dots, D_{n}f$. The partial derivative of such a scalar field (being already a partial derivative) is called a **second-order partial derivative of $f$**.
>>[!remark]
>>For functions of two variables, there are four second-order partial derivatives
>>$$\begin{align}
>> D_{1}(D_{1}f) &=\frac{\partial^2f}{\partial x^2} \\
>> D_{1}(D_{2}f) &=\frac{\partial^2f}{\partial x \partial y} \\
>> D_{2}(D_{1}f) &=\frac{\partial^2f}{\partial y \partial x} \\
>> D_{2}(D_{2}f) &=\frac{\partial^2f}{\partial y^2} \\
>>\end{align}$$

>[!def] Definition Total Derivative ([[../../../Sources/apostol1967.pdf#page=283|Source]])
>
>>[!remark]- Motivation
>>Recall that the derivative in real analysis determines the infinitely small change of a function $f$ around a point $a$. The derivative of a function $f: \mathbb{R} \rightarrow \mathbb{R}$ is defined as
>>$$\frac{df(x)}{dx} =\lim_{ h \to 0 } \frac{f(x + h) - f(x)}{h}$$
>>It determines the change of values around the point $x$ as we close in on the mapping of the change. Now denote
>>$$E(a,h) = \frac{f(a)+h -f(a)}{h}-f'(a)$$
>>with $h \neq 0$ and $E(a,0)=0$. This formula denotes the difference between the first derivative and the change of the mapping $f$ with respect to the change $h$ on $a$. Rearranging this formula yields
>>$$f(a+h)= f(a)+f'(a)h + hE(a,h)$$
>>Note, this equation is the first order [[Differentiation#^916fa1 | Taylor series expansion ]] of $f$ centered at $a$. Note, this equation now holds for $h=0$. Further, the term $hE(a,h)$ denotes the error committed by the approximation of the Taylor series expansion. As $h\to_{0}$ the error decreases as well.
>
>Let 
>- $f: S \to \mathbb{R}$ be a scalar field with $S \subseteq \mathbb{R}^n$
>- $\mathbf{a} \in S \subseteq \mathbb{R}^n$ be an interior point of $S$
>- $B(\mathbf{a}; r)$ be an $n$-ball in $S$
>- $\mathbf{v} \in \mathbb{R}^n$ with $\lvert\lvert v \rvert\rvert<r$ such that $(\mathbf{a}+\mathbf{v})\in B(\mathbf{a}; r)$
>
>We say $f$ is differentiable at $\mathbf{a}$ if there exists a linear transformation
>$$T_{\mathbf{a}}: \mathbb{R}^n \to \mathbb{R}$$
>and a scalar function
>$$ E:\mathbb{R}^n \times \mathbb{R}^{n} \to \mathbb{R}$$
>such that
>$$f(\mathbf{a}+\mathbf{v}) = f(\mathbf{a})+ T_{\mathbf{a}}(\mathbf{v}) + \lvert\lvert \mathbf{v} \rvert\rvert E(\mathbf{a},\mathbf{v})$$
>where $E(\mathbf{a}, \mathbf{v}) \to 0$ as $\lvert\lvert v \rvert\rvert \to 0$. The linear transformation $T_{\mathbf{a}}$ is called the total derivative of $f$ at $\mathbf{a}$.

>[!theorem] Theorem ([[../../../Sources/apostol1967.pdf#page=284|Source]])
>Assume $f$ is differentiable at $\mathbf{a}$ with total derivative $T_{\mathbf{a}}$. Then the derivative $f'(\mathbf{a}; \mathbf{y})$ exists for every $\mathbf{y} \in \mathbb{R}^n$, and we have
>$$T_{\mathbf{a}}(\mathbf{y}) = f'(\mathbf{a}; \mathbf{y})$$
>Moreover, $f'(\mathbf{a};\mathbf{y})$ is a linear combination of the components of $\mathbf{y}$. We have
>$$f'(\mathbf{a}; \mathbf{y}) = \sum_{k=1}^n D_{k}f(\mathbf{a})y_{k}$$
>>[!proof]-
>> If $\mathbf{y}=\mathbf{0}$ we have $T_{\mathbf{a}}(\mathbf{0})= 0$ due to linearity of $T_{\mathbf{a}}$, as well does $f'(\mathbf{a}, \mathbf{0}) = 0$ by [[Multivariate Calculus#^c18601 | definition]]. Assume now $\mathbf{y}\neq \mathbf{0}$. Since $f$ is differentiable at $\mathbf{a}$ we can state the first order [[Differentiation#^916fa1|Taylor series expansion]] of $f$ around the point $\mathbf{a}$ as
>> $$\begin{alignat}{3}
>> f(\mathbf{a} + \mathbf{v}) &= f(\mathbf{a} + \mathbf{v}) &&+ \underbrace{ f'(\mathbf{a} + \mathbf{v}) }_{ T_{\mathbf{a}}(\mathbf{v}) } &&+ \lvert\lvert \mathbf{v} \rvert\rvert E(\mathbf{a, \mathbf{ v}}) \\
>> &=f(\mathbf{a}) &&+ T_{\mathbf{a}}(\mathbf{v}) &&+ \lvert\lvert \mathbf{v} \rvert\rvert E(\mathbf{a, \mathbf{ v}}) \tag{by definition}
>>\end{alignat}$$
>>where $E$ is the error term from the approximation. Note, the error term holds the removed $\mathbf{v}$ from the first term. Now we take $\mathbf{v}=h\mathbf{y}$ with $h \neq 0$ and $\lvert h \rvert\lvert\lvert \mathbf{y} \rvert\rvert < r$, such that the mapping is still contained inside the $n$-ball around $\mathbf{a}$. Note, $T_{\mathbf{a}}$ is linear, i.e.
>>$$T_{\mathbf{a}}(\mathbf{v})= T_{\mathbf{a}}(h\mathbf{y}) = hT_{\mathbf{a}}(\mathbf{y})$$
>>Therefore, we write
>>$$\begin{align}
>> f(\mathbf{a} + \mathbf{v}) &= f(\mathbf{a}) + T_{\mathbf{a}}(\mathbf{v})+ \lvert\lvert \mathbf{v} \rvert\rvert E(\mathbf{a, \mathbf{ v}})  \\
>> f(\mathbf{a} +h\mathbf{y}) &= f(\mathbf{a}) + hT_{\mathbf{a}}(\mathbf{y})+ \lvert h \rvert \lvert\lvert \mathbf{y} \rvert\rvert E(\mathbf{a, \mathbf{ v}})  \\
>> f(\mathbf{a} +h\mathbf{y}) - f(\mathbf{a}) &= hT_{\mathbf{a}}(\mathbf{y})+ \lvert h \rvert \lvert\lvert \mathbf{y} \rvert\rvert E(\mathbf{a, \mathbf{ v}})  \\ \\
>> \frac{f(\mathbf{a} +h\mathbf{y}) - f(\mathbf{a}) }{h}&= T_{\mathbf{a}}(\mathbf{y})+ \lvert h \rvert \frac{\lvert\lvert \mathbf{y} \rvert\rvert E(\mathbf{a, \mathbf{ v}})}{h}
>>\end{align}$$
>> As $h \to 0$ we yield the expression given in the theorem
>> For the second part we use the linearity of $T_{\mathbf{a}}$ again, hence
>> $$\begin{align}
>> T_{\mathbf{a}} &= T_{\mathbf{a}}\left(\sum_{k=1}^n y_{k} \mathbf{e}_{k}\right) \\
>>  &= \sum_{k=1}^ny_{k}T_{\mathbf{a}}\left(\mathbf{e}_{k}\right) \\
>>  &= \sum_{k=1}^ny_{k}f'(\mathbf{a}; \mathbf{e}_{k}) \tag{definition partial derivative}\\
>>  &= \sum_{k=1}^ny_{k}D_{k}f(\mathbf{a}) \tag*{$\square$}\\
>>\end{align}$$