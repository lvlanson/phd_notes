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
| Vector Valued Function $\mathbf{f}$ <br>or Vector Field  | $\mathbf{f}:\mathbb{R}^n \rightarrow \mathbb{R}^m$ with $m,n > 1$                  |
| Components                                      | If $\mathbf{f}$ is a vector field, then $f_i \in \mathbf{f}$ is called a component | 

>[!def] Definition Open Ball ([[../../../Sources/apostol1967.pdf#page=269|Source]])
>Let $\mathbf{a} \in \mathbb{R}^n$ with $r>0$. The set $\mathbf{x} \in\mathbb{R}^n$ satisfying
>$$ \lvert\lvert \mathbf{x} -\mathbf{a} \rvert\rvert < r$$
>is called the **open $n$-ball**. We denote it
>$$ B(\mathbf{a}, r) = \{ \mathbf{x} \in \mathbb{R}^n \; \Big\vert \; \lvert\lvert \mathbf{x} - \mathbf{a} \rvert\rvert < r \}$$

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

^f5793c

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
>>  &= \sum_{k=1}^ny_{k}D_{k}f(\mathbf{a}) 
>>\end{align}$$
>>$$\begin{align}
>>\,\tag*{$\square$}\\
>>\end{align}$$
>
>>[!example] Example $f(x,y) = x^2 + y^2$
>>$$\begin{align}
>>df &= \frac{\partial f}{\partial x} dx + \frac{\partial f}{\partial y} dy \\
>> &= 2x^2 dx +2y^2dy
>>\end{align}$$
>
>>[!note]
>>The terms $dx$ and $dy$ represent infinitely small values. Note, if we consider the derivative of a function on the real line $f: \mathbb{R}\to \mathbb{R}$
>>$$\begin{align}
>>\frac{df}{dx} &= \frac{\partial f}{\partial x} \qquad&&\Big\vert \cdot dx \\
>> df &= \frac{\partial f}{\partial x} dx 
>>\end{align}$$
>>Note, that the infinitely small change in $f$ is equal to the derivative of $f$ with respect to $x$ times an infinitely small change in $x$, i.e. $dx$.
>>
------
>[!lemma] Lemma ([[../../../Sources/shifrin2005.pdf#page=112|Source]])
> Suppose $\mathbf{g}:[a,b] \to \mathbb{R}^n$ is continuous. Then, defining the integral of $\mathbf{g}$ component by component, i.e.
> $$\int _{a}^b \mathbf{g}(t) \, dt = \left[\begin{matrix}\int _{a}^b g_{1}(t)\, dt \\ \vdots \\ \int _{a}^b g_{n}(t)\, dt  \\
>\end{matrix}\right] $$
>we have the following property
>$$\left\lvert \left\lvert  \int _{a}^b \mathbf{g}(t) \, dt   \right\rvert \right\rvert \leq \int _{a}^b \lvert\lvert \mathbf{g}(t) \rvert\rvert  \, dt $$
>>[!proof]-
>>Let $$\begin{align}
>> \mathbf{v}=\int _{a}^b \mathbf{g}(t) \,dt \tag{1}
>>\end{align}$$
>>If $\mathbf{v}=\mathbf{0}$, both sides are equal. By the Cauchy-Schwartz inequality, i.e. $$\lvert \mathbf{v} \cdot \mathbf{g}(t)\rvert \leq \lvert\lvert \mathbf{v} \rvert\rvert \, \lvert\lvert \mathbf{g}(t) \rvert\rvert  $$
>>Then we have
>>$$\begin{align}
>> \lvert\lvert \mathbf{v} \rvert\rvert^2 &= \mathbf{v} \cdot \int _{a}^b \mathbf{g}(t)\, dt  \tag*{by equation (1)}  \\
>>          &= \int _{a}^b\mathbf{v} \cdot \mathbf{g}(t)\, dt \\
>>          &\leq \int _{a}^b \lvert\lvert \mathbf{v}  \rvert\rvert \, \lvert\lvert \mathbf{g}(t) \rvert\rvert \, dt \tag*{Cauchy-Schwartz}\\
>>          &= \lvert\lvert \mathbf{v}  \rvert\rvert \int _{a}^b \lvert\lvert \mathbf{g}(t) \rvert\rvert \, dt \\
>>\end{align}$$
>>Hence, we have
>>$$\begin{alignat}{2}
>> \lvert\lvert \mathbf{v} \rvert\rvert^2 &\leq \lvert\lvert \mathbf{v}  \rvert\rvert \int _{a}^b \lvert\lvert \mathbf{g}(t) \rvert\rvert \, dt \qquad&&\Big\vert :\lvert\lvert v \rvert\rvert \tag{$\mathbf{v}\neq 0$} \\
>> \lvert\lvert \mathbf{v} \rvert\rvert &\leq \int _{a}^b \lvert\lvert \mathbf{g}(t) \rvert\rvert \, dt \tag*{$\square$} \\
>>\end{alignat}$$
>>^lemmamultiintegral

>[!def] Proposition Mean Value Inequality ([[../../../Sources/shifrin2005.pdf#page=262|Source]])
>Suppose $U \subset \mathbb{R}^n$ is open, $\mathbf{f}: U \to \mathbf{R}^m$ with $\mathbf{f}\in C^1$ and $\mathbf{a}, \mathbf{b} \in U$, such that the line segment between them is contained in $U$. Then
>$$\lvert\lvert \mathbf{f}(\mathbf{b}) - \mathbf{f}(\mathbf{a}) \rvert\rvert \leq \left(\underset{\mathbf{x}\in [\mathbf{a}, \mathbf{b}]}{\text{max}}\lvert\lvert D\mathbf{f}(\mathbf{x}) \rvert\rvert \right)\lvert\lvert \mathbf{b}-\mathbf{a} \rvert\rvert  $$
>
>>[!remark]
>> The **mean value inequality** is a generalization of the [[Differentiation#^d97652|mean value theorem]] defined on the real valued functions. This theorem tells us, that we have bounds on the size of the derivative of a differentiable function. Specifically it tells us how much a function can change from one point to another.
>>
>> The term $\underset{\mathbf{x}\in [\mathbf{a}, \mathbf{b}]}{\text{max}}\lvert\lvert D\mathbf{f}(\mathbf{x}) \rvert\rvert$ gives us the value of the most the function is stretching vectors along the line segment $\mathbf{b}-\mathbf{a}$ and multiplying it by how far we moved from one point to another.
>
>>[!proof]-
>>Let 
>>$$\mathbf{g}:[0,1] \to \mathbb{R}^m$$
>>with
>>$$\mathbf{g}(t)=\mathbf{f}(\mathbf{b}+t(\mathbf{a}-\mathbf{a}))$$
>>Note that
>>$$\mathbf{f}(\mathbf{b}) - \mathbf{f}(\mathbf{a}) = \mathbf{g}(1) - \mathbf{g}(0)$$
>>$\mathbf{g}$ is differentiable, since it is defined by $\mathbf{f}\in C^1$. Differentiating using the chain rule yields
>>$$\begin{align}
>>\mathbf{g}'(t)= D\mathbf{f}\Big(\mathbf{a}+ t(\mathbf{b}-\mathbf{a})\Big)(\mathbf{b}-\mathbf{a}) \tag{1}
>>\end{align}$$
>>Further we have 
>>$$\begin{align}
>>\mathbf{g}(1)-\mathbf{g}(0) &= \mathbf{f}(\mathbf{a}+(\mathbf{b}-\mathbf{a}))- \mathbf{f}(\mathbf{a}) \\\left(\underset{\mathbf{x}\in [\mathbf{a}, \mathbf{b}]}{\text{max}}\lvert\lvert D\mathbf{f}(\mathbf{x}) \rvert\rvert \right)\lvert\lvert \mathbf{b}-\mathbf{a} \rvert\rvert
>> &= \mathbf{f}(\mathbf{b})-\mathbf{f}(\mathbf{a})
>>\end{align}$$
>>Using this and [[#^lemmamultiintegral | the multivariate Cauchy Schwartz lemma on integrals]] 
>>$$\begin{align}
>> \lvert\lvert \mathbf{f}(\mathbf{b}) - \mathbf{f}(\mathbf{a}) \rvert\rvert &= \lvert\lvert \mathbf{g}(\mathbf{1}) - \mathbf{g}(\mathbf{0}) \rvert\rvert \tag{definition of $\mathbf{g}$}\\
>>  &= \left\lvert \left\lvert  \int _{0}^1 \mathbf{g}'(t) \, dt   \right\rvert \right\rvert \\
>>  &\leq  \int _{0}^1\left\lvert \left\lvert  \mathbf{g}'(t) \right\rvert \right\rvert  \, dt  \tag{Cauchy Schwartz with $\mathbf{v}=\mathbf{1}$}\\
>>  &\leq \underset{\mathbf{x}\in [\mathbf{a}, \mathbf{b}]}{\text{max}} \lvert\lvert \mathbf{g}'(t) \rvert\rvert 
>>\end{align}$$
>>Inserting the result of equation $(1)$
>>$$\begin{align}
>> \lvert\lvert \mathbf{g}'(t) \rvert\rvert &\leq \lvert\lvert D\mathbf{f}(\mathbf{a}+t(\mathbf{b}-\mathbf{a})) \rvert\rvert\,\lvert\lvert \mathbf{b}-\mathbf{a} \rvert\rvert    \\
>> \underset{t\in [0,1]}{\text{max}}\lvert\lvert \mathbf{g}'(t) \rvert\rvert &\leq  \left(\underset{\mathbf{x}\in [\mathbf{a}, \mathbf{b}]}{\text{max}}\lvert\lvert D\mathbf{f}(\mathbf{x}) \rvert\rvert \right)\lvert\lvert \mathbf{b}-\mathbf{a} \rvert\rvert \tag*{$\square$}
>>\end{align}$$
>
>>
>>

^74523c

>[!def] Definition Contraction Map ([[../../../Sources/shifrin2005.pdf#page=259|Source]])
>Let $X$ be a subset of $\mathbb{R}^n$. A function $\mathbf{f}: X \to X$ is called a **contraction mapping** if there is a constant $c$ with $0 < c < 1$, such that
>$$\begin{align}
> \lvert\lvert \mathbf{f}(\mathbf{x}) - \mathbf{f}(\mathbf{y}) \rvert\rvert \leq c \lvert\lvert \mathbf{x}-\mathbf{y} \rvert\rvert  
>\end{align}$$
>for all $\mathbf{x}, \mathbf{y} \in X$
>>[!proof]
>>Let $\mathbf{x}_{0}\in X$ be arbitrary, and define a sequence recursively by 
>>$$\mathbf{x}_{k+1}= \mathbf{f}(\mathbf{x}_{k})$$

>[!Theorem] Proposition Absolute Convergence ([[../../../Sources/shifrin2005.pdf#page=258|Source]])
>  Let $(\mathbf{a}_{k})_{k=1}^\infty \subseteq \mathbb{R}^n$ with
>  $$\sum_{k=1}^\infty \lvert\lvert  \mathbf{a}_{k} \rvert\rvert $$ 
> is convergent. Then the series
> $$\sum_{k=1}^\infty \mathbf{a}_{k}$$
> is convergent too.
>>[!proof]-
>> First consider the case of $\mathbb{R}^n = \mathbb{R}$. We define the following sequence, 
>> $$\begin{align}
>> b_{k} = a_{k} + \lvert a_{k} \rvert \tag{1}
>>\end{align}$$
>> Note,
>> $$b_{k} = \begin{cases}
>> 2a_k, & \text{ if } a_{k} \geq 0 \\
>> 0, & \text{ else }
>>\end{cases}$$
>>Since by assumption that $\sum_{k=1}^{\infty} \lvert a_{k} \rvert$ is convergent, the series $\sum_{k=1}b_{k}$ must be convergent, since
>>$$\sum_{k=1}^\infty b_{k} = \begin{cases}
>> \sum_{k=1}^\infty 2\lvert a_{k} \rvert & \text{ if } a_{k}>0 \\
>> 0 & \text{ else}
>>\end{cases}$$
>>Since $\sum_{k=1}^{\infty} \lvert a_{k} \rvert$ is convergent, $\sum_{k=1}^\infty b_{k}$ must be convergent too with upper bound $2\sum_{k=1}^\infty \lvert a_{k} \rvert$. Rearranging equation $(1)$ gives
>>$$\begin{align}
>>a_{k} = b_{k} + \lvert a_{k} \rvert 
>>\end{align}$$
>>Hence, $\sum_{i=1}^\infty a_{k}$ must converge, since it's the sum of two converging series.
>>
>>We generalize now this result on $\mathbb{R}^n$. Let $a_{k, j}$ denote the $k$-th vector in the sequence $(\mathbf{a}_{k})_{k=1}^\infty$ and there the $j$-th component, i.e. $$\underbrace{ \mathbf{a}_{k} }_{ \in (\mathbf{a}_{k})_{k=1}^\infty} = (a_{1}, \dots, \underbrace{ a_{j} }_{ = a_{k,j} }, \dots)$$
>> Note that
>> $$\lvert a_{k,j} \rvert \leq \lvert\lvert \mathbf{a}_{k} \rvert\rvert  $$
 >>From this we can conclude
 >>$$\sum_{k=1}^\infty \lvert a_{k,j} \rvert \leq \sum_{k=1}^\infty \lvert\lvert \mathbf{a}_{k} \rvert\rvert $$
 >>Therefore, as shown in the case of $\mathbb{R}$, $\sum_{k=1}^\infty a_{k,j}$ must be convergent. This is true for any $j = 1, \dots, n$, i.e.
 >>$$\sum_{k=1}^\infty \mathbf{a}_{k} = \left[\begin{matrix}
>> \sum_{k=1}^\infty a_{k,1}  \\
>> \vdots \\
>> \sum_{k=1}^\infty a_{k,n}
>>\end{matrix}\right]$$
>>must be convergent too.
>>$$\begin{align}
>>\,\tag*{$\square$}
>>\end{align}$$

^62fac3

>[!theorem] Theorem Contraction Mapping Principle ([[../../../Sources/shifrin2005.pdf#page=259|Source]])
>Let $X \subset \mathbb{R}^n$ be closed. Let $\mathbf{f}: X \to X$ be a contraction mapping. Then there is a unique point $\mathbf{x} \in X$ such that $\mathbf{f}(\mathbf{x})=\mathbf{x}$.
>>[!note]
>>$\mathbf{x}$ is called a fixed point of $\mathbf{f}$.
>
>>[!proof]-
>>>[!note] Plan
>>>We want to show that $\mathbf{f}$ is a contraction mapping as the sequence will converge to a point $\mathbf{x}\in X$ using the continuity of $\mathbf{f}$ with
>>>$$ \mathbf{f}(\mathbf{x}) = \lim_{ k \to \infty } \mathbf{f}(\mathbf{x}_{k})=\lim_{ k \to \infty } \mathbf{x_{k+1}}=\mathbf{x}$$
>>
>>Consider the equation
>>$$\begin{align}
>>\mathbf{x}_{k} &= \mathbf{x}_{0} + (\mathbf{x}_{1} - \mathbf{x}_{0}) + (\mathbf{x}_{2} - \mathbf{x}_{1}) + \dots + (\mathbf{x}_{k} - \mathbf{x}_{k-1})  \\
>>   &= \mathbf{x}_{0} + \sum_{j=1}^k (\mathbf{x}_{j} - \mathbf{x}_{j-1}) \\
>>\end{align}$$
>>We can formulate each element with
>>$$\mathbf{a}_{k} = \mathbf{x}_{k}-\mathbf{x}_{k-1}$$
>>with $k>1$. We want to estimate $\lvert\lvert \mathbf{a}_{k} \rvert\rvert$
>>$$\begin{align}
>>\lvert\lvert \mathbf{a}_{k} \rvert\rvert &= \lvert\lvert \mathbf{x}_{k}-\mathbf{x}_{k-1} \rvert\rvert =\lvert\lvert \mathbf{f}(\mathbf{x}_{k-1})-\mathbf{f}(\mathbf{x}_{k-2}) \rvert\rvert    \\
>> &\leq c\lvert\lvert \mathbf{x}_{k-1}-\mathbf{x}_{k-2} \rvert\rvert \\
>>\lvert\lvert \mathbf{a}_{k} \rvert\rvert&\leq c\lvert\lvert \mathbf{a}_{k-1} \rvert\rvert \tag{1}
>>\end{align}$$
>>for some constant $0 < c < 1$. The contraction mapping principle can be seen by applying equation $(1)$ over and over again
>>$$\begin{align}
>> \lvert\lvert \mathbf{a}_{k} \rvert\rvert \;\leq\; c \lvert\lvert \mathbf{a}_{k-1} \rvert\rvert \;\leq\; c^2 \lvert\lvert \mathbf{a}_{k-2} \rvert\rvert \;\leq\; \dots \;\leq\; c^{k-1} \lvert\lvert \mathbf{a}_{1} \rvert\rvert
>>\end{align}$$
>>Therefore, we have
>>$$\begin{align}
>> \sum^K_{k=1} \lvert\lvert \mathbf{a} _{k}\rvert\rvert &\leq \left(\sum^K_{k=1}c^{k-1}\right)\lvert\lvert \mathbf{a}_{1} \rvert\rvert \\ 
>> &=\frac{1-c^K}{1-c}\lvert\lvert \mathbf{a}_{1} \rvert\rvert 
>>\end{align}$$
>>Since $0 < c < 1$ we see $c^K$ vanishing as $K \to \infty$, therefore we have
>>$$\lim_{ K \to \infty } \frac{1-c^K}{1-c} = \frac{1}{1-c}$$
>>Therefore, we can conclude the series $\sum_{k=1}^\infty \lvert\lvert \mathbf{a}_{k} \rvert\rvert$ converges, and hence $\sum_{k=1}^\infty \mathbf{a}_{k}$ converges too by [[#^62fac3 | the proposition about absolute convergence]]. Therefore, $$\mathbf{x}_{k} \to \mathbf{x}_{0}+\mathbf{a} = \mathbf{x}$$
>>Since all $\mathbf{x}_{k} \in X$ and $X$ is closed, $\mathbf{x} \in X$.
>> 

^7623e0


>[!theorem] Inverse Function Theorem ([[../../../Sources/shifrin2005.pdf#page=266|Source]], [Video Source](https://youtu.be/CUZnkWa0Mr0?si=jMAR5W7H41a1WOlf), [Video Source Proof](https://youtu.be/LkUl8HTIJM4?si=NiuNRX0_Ds9o6-A6))
>Suppose $U \subset \mathbb{R}^n$ is open and $\mathbf{f}: U \to \mathbb{R}^n$ is a vector field with $\mathbf{f} \in C^1$ with $D\mathbf{f}$ being invertible in $\mathbf{x}_{0} \in U$. Then there is a neighborhood $V \subset U$ of $\mathbf{x}_{0}$ on which $\mathbf{f}$ has a $C^1$ inverse function. That is, there are neighborhoods $V$ of $\mathbf{x}_{0}$ and $W$ of $\mathbf{f}(\mathbf{x}_{0}) = \mathbf{y}_{0}$ and a $C^1$ function $\mathbf{g}: W \to V$ such that
>$$ \mathbf{f}(\mathbf{g}(\mathbf{y})) = \mathbf{x}\qquad \forall \mathbf{y} \in W$$
>and
>$$\mathbf{g}(\mathbf{f}(\mathbf{x})) = \mathbf{y} \qquad \forall \mathbf{x} \in V$$
>Moreover, if $\mathbf{f}(\mathbf{x}) =  \mathbf{y}$, we have
>$$D\mathbf{g}(\mathbf{y}) = (D\mathbf{f}(\mathbf{x}))^{-1}$$
>>[!note]
>>The mapping matches dimensions of its domain and codomain. Both have dimension $n$.
>
>>[!remark] Remark on the Inverse Function Theorem
>> The last equation can be obtained $\forall \mathbf{x} \in V$ with
>> $$\begin{align}
>> \mathbf{g}(\mathbf{f}(\mathbf{x})) &= \mathbf{x}  \\
>> D\mathbf{g}(\mathbf{f}(\mathbf{x})) &= D\mathbf{x} \tag{Total Derivative with respect to $\mathbf{x}$}\\ 
>> \mathbf{g}'(\mathbf{f}(\mathbf{x}))f'(\mathbf{x}) &= \mathbf{1} \tag{Chain Rule} \\
>> \mathbf{g}'(\mathbf{f}(\mathbf{x})) &= \frac{\mathbf{1}}{\mathbf{f}'(\mathbf{x})}
>>\end{align} $$
>
>>[!proof]
>>>[!Note] Plan
>>>![[figures/inverse_function_theorem_proof.jpg]]
>>> We want to show there are open sets around $\mathbf{0}$ such that for every $\mathbf{y}$ near $\mathbf{0}$ in range of some closed ball $B(\mathbf{0}; r)$, there is some **unique** $\mathbf{x}_{\mathbf{y}}$ near $\mathbf{0}$ in the domain of $\mathbf{f}(\mathbf{x}_{\mathbf{y}})= \mathbf{y}$. So if we vary the $\mathbf{y}$ we will get a different $\mathbf{x}$.
>>>
>>>We will try to convert the problem $\mathbf{f}(\mathbf{x})=\mathbf{y}$ into a fixed point problem such that
>>>$$\phi_{{\mathbf{y}}}(\mathbf{x}) = \mathbf{x} \underbrace{ - \mathbf{f}(\mathbf{x})+\mathbf{y} }_{ =\mathbf{0} }$$
>>>We will further define $D\mathbf{f}(\mathbf{0}) = \mathbf{1}$ and we require our operations to be in the defined subsets. Therefore we choose $-\mathbf{f}(\mathbf{x})+\mathbf{y}$ over $\mathbf{f}(\mathbf{x})-\mathbf{y}$ to have better control over the conditions we chose for our proof.
>>
>> Without loss of generality, let 
>> - $\mathbf{a} = \mathbf{0}$
>> - $\widehat{\mathbf{f}}(\mathbf{a})=\mathbf{0}$
>> - $D\mathbf{f}(\mathbf{0}) =\mathbf{1}$
>>
>>>[!note]
>>>This is just a change of coordinates. Note, if we'd map any $\mathbf{f}(\mathbf{x}) = \mathbf{y}$, we would now shift the mapping by $\mathbf{a}$ to yield the same result, i.e.
>>>$$\mathbf{f}(\mathbf{x})= \widehat{\mathbf{f}}(\mathbf{x}+\mathbf{a})- \mathbf{f}(\mathbf{a})$$
>>
>>We can choose $r >0$ such that
>>$$ \lvert\lvert D\mathbf{f}(\mathbf{x})- \mathbf{1} \rvert\rvert \leq \frac{1}{2} $$
>>for $\lvert\lvert \mathbf{x} \rvert\rvert \leq r$. Further we fix $\mathbf{y}$ with $$\lvert\lvert \mathbf{y} \rvert\rvert \leq \frac{r}{2}$$
>>Also, we now define the map for the fixed point problem
>>$$\phi(\mathbf{x}) = \mathbf{x} - \mathbf{f}(\mathbf{x}) + \mathbf{y}$$
>>Note that the total derivative with respect to $\mathbf{x}$ is
>>$$\begin{align}
>> \lvert\lvert D\phi(\mathbf{x}) \rvert\rvert &=\lvert\lvert D(\mathbf{x}- \mathbf{f}(\mathbf{x}) + \mathbf{y}) \rvert\rvert \tag{$\mathbf{y}$ is fixed}\\
>>  &=\lvert\lvert \mathbf{1}- D\mathbf{f}(\mathbf{x}) \rvert\rvert \\ 
>>  &= \lvert\lvert D\mathbf{f}(\mathbf{x})-\mathbf{1} \rvert\rvert \tag{1}
>>\end{align}$$
>>Whenever $\lvert\lvert \mathbf{x} \rvert\rvert \leq r$. We have by the [[#^74523c | mean value inequality]]
>>$$\begin{align}
>> \lvert\lvert \phi(\mathbf{x}) \rvert\rvert &= \lvert\lvert \phi(\mathbf{x}) - \phi(\mathbf{0}) + \mathbf{y}\rvert\rvert   \\
>> \lvert\lvert \phi(\mathbf{x}) \rvert\rvert &\leq \lvert\lvert \phi(\mathbf{x}) - \phi(\mathbf{0})\rvert\rvert + \rvert\rvert\mathbf{y}\rvert\rvert   \\
>> &= \left(\underset{\mathbf{x}\in [\mathbf{0}, \mathbf{x}]}{\text{max}}\lvert\lvert D\phi(\mathbf{x}) \rvert\rvert \right)+\lvert\lvert \mathbf{x} - \mathbf{0} \rvert\rvert  \lvert\lvert \mathbf{y} \rvert\rvert  \tag{Mean-Value Inequality} \\ 
>> &= \left(\underset{\mathbf{x}\in [\mathbf{0}, \mathbf{x}]}{\text{max}}\underbrace{ \lvert\lvert D\mathbf{f}(\mathbf{x})-\mathbf{1} \rvert\rvert }_{ \leq \frac{1}{2} }  \right) \underbrace{ \mathbf{\lvert\lvert x \lvert\rvert } }_{ =r }+ \underbrace{ \lvert\lvert \mathbf{y} \rvert\rvert }_{ < \frac{r}{2} }   \\ 
>> &< \frac{r}{2}+\frac{r}{2}=r 
>>\end{align}$$
>>>[!note]
>>>We constructed $\phi(\mathbf{x})$ in such a way, that it maps from a ball into itself, but contracts by $1/2$. We had to add the term $\mathbf{y}$, such that it does not shift outside the ball, as can be seen when we used the trick to determine $\lvert\lvert \phi(\mathbf{x}) \rvert\rvert$ with the mean value inequality. Hence, our function $\phi_{\mathbf{y}}$ can be described as
>>>$$ \phi_{\mathbf{y}}: \overline{B}(\mathbf{0}, r) \to  \overline{B}(\mathbf{0}, r)$$
>>>We can easily confirm, that $\phi$ is a contraction map. We check that for some arbitrary points $\mathbf{a}, \mathbf{b} \in  \overline{B}(\mathbf{0}, r)$ they stay inside the ball by a constant factor. We have
>>>$$\begin{align}
>>> \lvert\lvert \phi_{\mathbf{y}}(\mathbf{b})-\phi_{\mathbf{y}}(\mathbf{a}) \rvert\rvert &= \Bigg(\underbrace{ \underset{\mathbf{x}\in [\mathbf{a}, \mathbf{b}]}{\text{max}}\lvert\lvert D\phi_{\mathbf{y}}(\mathbf{x}) \rvert\rvert }_{ \leq \frac{1}{2} } \Bigg)\lvert\lvert \mathbf{b}-\mathbf{a} \rvert\rvert   \\
>>> &\leq \frac{1}{2}\lvert\lvert \mathbf{b}-\mathbf{a} \rvert\rvert 
>>>\end{align}$$
>>
>>Since $\phi$ is a contraction map as shown in the note, we know that by [[#^7623e0 | contraction mapping principle]] there exists some unique fixed point $\mathbf{x}_{\mathbf{y}} \in \overline{B}(\mathbf{0}; r)$, such that $\mathbf{f}(\mathbf{x}_{\mathbf{y}})=\mathbf{y}$

^7137a9

