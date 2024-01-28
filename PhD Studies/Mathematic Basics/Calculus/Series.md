>[!def] Definition Power Series ([[../../../Sources/zotero-182.pdf#page=540 | Source 1]], [[../../../Sources/briggs2019.pdf#page=733 | Source 2]], [[../../../Sources/rudin1976.pdf#page=79 | Source 3]])
>A series of the form
>$$\sum_{n=0}^\infty c_{n}x^n = c_{0} + c_{1}x + c_{2}x^2+ \dots$$
>is a power series centered at $x=0$. A series of the form
>$$\sum_{n=0}^\infty c_{n}(x-a) = c_{0} + c_{1}(x-a)+c_{2}(x-a)^2+\dots$$
>is a power series centered at $x=a$.

^588b80

>[!theorem] Theorem Convergence of a Power Series ([[../../../Sources/zotero-182.pdf#page=541 | Source 1]], [[../../../Sources/rudin1976.pdf#page=79 | Source 2]])
> Consider the power series $\sum_{n=0}^\infty c_{n}(x-a)^n$. The series satisfies exactly one of the following properties:
> 1. The series converges at $x = a$ and diverges for all $x \neq a$ 
> 2. The series converges for all real numbers $x$.
> 3. The exists a real number $R>0$ such that the series converges if $\lvert x-a \rvert < R$ and diverges if $\lvert x-a \rvert > R$. At the values $x$ where $\lvert x-a \rvert = R$, the series may converge or diverge.
> 
>>[!proof]-
>>Suppose the power series is centered at $a=0$. We first show that
>>> if there exists a real number $d \neq 0$ such that $\sum_{n=0}^\infty c_{n}d^n$ converges, then the series $\sum_{n=0}^\infty x^n$ converges absolutely for all $x$ such that $\lvert x \rvert < \lvert d \rvert$. 
>>> <u>Proof</u>
>>> Since $\sum_{n=0}^\infty c_{n}d^n$ converges, there exists some integer $N$ with $n \geq N$ such that $\lvert c_{n}d^n \rvert \leq 1$. We have
>>> $$\lvert c_{n}x^n \rvert = \lvert c_{n}d^n \rvert \; \left\lvert  \frac{x}{d}   \right\rvert^n $$
>>> Note $c_{n}\cancel{ d^n }\; \frac{x^n}{\cancel{ d^n }}$. Since $\lvert c_{n}d^n \rvert \leq 1$ for $n \geq N$, we can conclude
>>> $$\lvert c_{n}x^n \rvert \leq \left\lvert  \frac{x}{d}  \right\rvert^n  $$
>>> Now we state
>>> $$\sum_{n=N}^\infty \left\lvert  \frac{x}{d}  \right\rvert^n$$
>>> is a geometric series that is convergent if $\left\lvert  \frac{x}{d}  \right\rvert<1$. By the comparison test, we conclude that $\sum_{n=N}^\infty c_{n}x^n$ also converges for $\lvert x \rvert<\lvert d \rvert$. Since we can add finite many terms to a convergent series, we can conclude that $\sum_{n=0}^\infty c_{n}x^n$ converges for $\lvert x \rvert < \lvert d \rvert$.
>>> $$\begin{align}
>>>\, \tag*{$\square$}
>>>\end{align}$$
>> 
>> Let $S$ be a set of real numbers, such that the series converges.
>> 1. $S=\{ 0 \}$
>> 2. $S=\mathbb{R}$
>> 3. Assume $S\neq \{ 0 \}$ and $S\neq \mathbb{R}$, then there exists a real number $x^* \neq 0$ such that the series does not converge. The series cannot converge for any $x$ such that $\lvert x \rvert> \lvert x^* \rvert$. Therefore, $S$ must be bounded. Hence, the series converges by some smallest upper bound $R$ with $\lvert x \rvert < R$.

>[!def] Definition Taylor/Maclaurin Series for a Function ([[../../../Sources/briggs2019.pdf#page=756 | Source]])
>Suppose the function $f$ has derivatives of all orders on an interval centered at the point $a$. The **Taylor series for $f$ centered at $a$** is
>$$\sum_{k=0}^\infty \frac{f^{k}(a)}{k!}(x-a)^k= f(a) + f'(a)(x-a)+ \frac{f''(a)}{2!}(x-a)^2 +\dots$$
>>[!remark]
>>A Taylor Series centered at $a=0$ is called a Maclaurin series.

^916fa1

>[!def] Definition $n$-th Taylor/Maclaurin Polynomial
>If $f$ has $n$ derivatives at $x=a$, then the $n$-th Taylor polynomial for $f$ at $a$ is
>$$p_{n}(x)=f(a)+f'(a)(x-a)+\frac{f''(a)}{2!}(x-a)^2 + \dots + \frac{f^{(n)}(a)}{n!}(x-a)^n$$
>>[!remark]
>>The $n$-th Taylor polynomial for $f$ at $0$ is known as the $n$-th Maclaurin polynomial for $f$.

^78a81b

>[!def] Definition Exponential Function ([[../../../Sources/zotero-182.pdf#page=572| Source]])
>The exponential function $e^x$ can be expressed as Maclaurin series
>$$e^x = \sum_{n=0}^\infty \frac{x^n}{n!}$$
>>[!remark]
>>Assume $x=1$ we have
>>$$e=\sum_{n=0}^\infty \frac{1}{n!}$$
>
>>[!proof]- Construction
>> Note, since the exponential function will be represented as a Maclaurin series, it will be centered at $a=0$. Further, we know that for $f(x) = e^x$
>> $$f(x) = f'(x) = f''(x) = \dots = f^{(n)}(x)$$
>> Therefore, for the Maclaurin series centered at $a=0$, we have
>> $$f(0) = f'(0) = f''(0) = \dots = f^{(n)}(0) = 1$$
>> The $n$-th Maclaurin polynomials can be built as follows
>> $$\begin{align}
>> p_{0}(x) &= f(0) = 1  \\
>> p_{1}(x) &= f(0) + f'(0)x  \\
>>       &= 1 + x \\
>> p_{2}(x) &= f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 \\
>>       &= 1 + x + \frac{1}{2}x^2 \\
>> p_{3}(x) &= f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \frac{f''(0)}{3!}x^3  \\
>>       &= 1 + x + \frac{1}{2}x^2 + \frac{1}{3!}x^3 \\
>> &\vdots \\
>> p_{n}(x) &= f(0) + f'(0)x + \frac{f''(0)}{2!}x^2 + \frac{f''(0)}{3!}x^3 + \dots + \frac{f^{(n)}}{n!}x^n \\ \\
>>       &= 1 + x + \frac{x^2}{2} + \frac{x^3}{3!} + \dots +  \frac{x^n}{n!} \\
>>       &= \sum_{k=0}^n \frac{x^k}{k!}
>>\end{align}$$

^9251bc

