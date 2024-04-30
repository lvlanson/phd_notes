>[!def] Definition The Derivative Function ([[../../../PDFs/briggs2019.pdf#page=167| Source]])
>The **derivative** of $f$ is the function
>$$f'(x)=\lim_{ h \to 0 } \frac{f(x+h)-f(x)}{h}$$

^6875e0

>[!theorem] Theorem Differentiable Implies Continuity ([[../../../PDFs/briggs2019.pdf#page=172| Source]])
>If $f$ is differentiable at $a$, then $f$ is continuous at $a$
>>[!proof]-
>>Since $f$ is differentiable at $a$ the [[#^6875e0| derivative]] exists, hence
>>$$f'(a)= \lim_{ x \to a } \frac{f(x)-f(a)}{x-a}$$
>>To show that $f$ is continuous at $a$ we need to show that $f(a) = \lim_{ x \to a }f(x)$. Note the following identity for $x \neq a$
>>$$\begin{align}
>> f(x) &= f(x) \\
>>  &= \frac{f(x)(x-a)}{x-a} \\
>>  &= \frac{f(x)(x-a)}{x-a} +f(a)-f(a)\\
>>  &= \frac{f(x)(x-a)-f(a)(x-a)}{x-a} +f(a)\\
>>  &= \frac{f(x)-f(a)}{x-a}(x-a) +f(a)\\
>>\end{align}$$
>>Now we take the limit $x\to a$
>>$$\begin{align}
>> \lim_{ x \to a }f(x) &= \lim_{ x \to a }\left(\frac{f(x)-f(a)}{x-a}(x-a) +f(a)\right)  \\
>> &= \underbrace{ \lim_{ x \to a } \left(\frac{f(x)-f(a)}{x-a}\right) }_{ =f'(a) }\underbrace{ \lim_{ x \to a } (x-a) }_{ =0 }+\underbrace{ \lim_{ x \to a } f(a) }_{ =f(a) } \\
>> &= f'(a)\cdot 0 + f(a) \\
>> &= f(a) \tag*{$\square$}
>>\end{align}$$

^35aeb2

>[!def] Definition Smooth Functions ([[../../../PDFs/howell2016.pdf#page=37| Source]])
>For a function $f$ to be smooth over an interval $(\alpha, \beta)$ it must satisfy two conditions:
>1. $f$ must be differentiable (and therefore continuous) everywhere on $(\alpha, \beta)$
>2. $f'$ must also be a continuous function on $(\alpha, \beta)$

>[!def] Definition Uniform Smooth Functions ([[../../../PDFs/howell2016.pdf#page=37| Source]])
>Let $(\alpha, \beta)$ be a finite interval. A function is uniformly smooth on $(\alpha, \beta)$ if and only if
>1. $f$ is smooth on $(\alpha, \beta)$ 
>2. both $f$ and $f'$ are uniformly continuous on $(\alpha, \beta)$

>[!def] Definition Piecewise Smooth Functions ([[../../../PDFs/howell2016.pdf#page=38| Source]])
>A function is said to be piecewise smooth over a finite interval $(\alpha, \beta)$ if and only if $(\alpha, \beta)$ can be partitioned into a finite number of subintervals over which the function is uniformly smooth.
>
>If $(\alpha, \beta)$ is an infinite interval, then a function is piecewise smooth over $(\alpha, \beta)$ if and only if it is piecewise smooth over every finite subinterval of $(\alpha, \beta)$

^680da2

>[!theorem] Rolle's Theorem ([[../../../PDFs/briggs2019.pdf#page=276| Source]])
>Let $f$ be continuous on a closed interval $[a,b]$ and differentiable on $(a,b)$ with $f(a) = f(b)$. There is at least one point $c$ in $(a,b)$ such that $f'(c) = 0$.
>
>![[figures/rolles_theorem.png | 350]]
>>[!proof]-
>>><u>Case 1:</u>
>>>Suppose $f$ attains both its absolute maximum and minimum values at the endpoints. Since $f(a) = f(b)$ the maximum and minimum are equal, and it follows that $f$ is a constant function, i.e. $f'(x) = 0$ for all $x \in (a,b$.
>>
>>><u>Case 2:</u>
>>>Assume at least one of the absolute extreme values of $f$ does not occur at an end-point, then $f$ must attain an absolute extreme value at an interior point of $[a,b]$. Therefore, $f$ must have either a local maximum or a local minimum at point $c \in (a,b)$.  An extremum $(x_{E}, y_{E})$ is known to satisfy
>>>$$ f'(x_{E})=0$$
>>>Therefore there exists some point with $f'(c)=0$ $$\begin{align}
>>> \,\tag*{$\square$}
>>>\end{align}$$

^5732a4

>[!theorem] Mean Value Theorem ([[../../../PDFs/briggs2019.pdf#page=277| Source]])
> If $f$ is continuous on the closed interval $[a,b]$ and differentiable on $(a,b)$, then there is at least on point $c$ in $(a,b)$ such that
> $$\frac{f(b)-f(a)}{b-a} = f'(c)$$
> 
> ![[figures/mean_value_theorem_real.png | center]]
>>[!proof]-
>> Note the secant line passes through the points $(a, f(a))$ and $(b, f(b))$. Let the secant line be described by the function $l(x)$. Further, we define a function $g(x)$ which measures the difference between the secant line and the original graph, i.e.
>> $$g(x) = f(x) - l(x)$$
>> Since $f$ and $l$ are continuous on $[a,b]$ and differentiable on $(a,b)$, it follows $g$ must also be continuous on $[a,b]$ and differentiable on $(a,b)$. Note, that both functions intersect at $f(a) = l(a)$ and $f(b) = l(b)$. Therefore, we can state
>> $$\begin{alignat}{2}
>> g(a) &= f(a)-l(a)  &&= 0\\
>> g(b) &= f(b)-l(b) &&= 0
>>\end{alignat}$$
>>Hence, equation $g(x)$ fulfills the condition of [[Differentiation Statements#^5732a4|Rolle's Theorem]]. Thus, there exists a point $c \in (a,b)$ such that $g'(c) = 0$.  Differentiating on both sides of $g$ we have
>>$$ g'(c) = f'(c) - l'(c) = 0$$
>>By this assertion we can conclude
>>$$ \begin{align}
>> f'(c) = l'(c) \tag{1}
>>\end{align} $$
>>Now we determine $l'(c)$. Note, the derivative of $l'(c)$ is the slope of the secant line. By definition, it is
>>$$l'(c) = \frac{f(b)-f(a)}{b-a}$$
>>From the result of equation $(1)$ we can conclude
>>$$ \begin{align}
>> f'(c) = \frac{f(b)-f(a)}{b-a} \tag*{$\square$}
>>\end{align}$$

^71d429

>[!theorem] Theorem L'Hospital's Rule ([[../../../PDFs/briggs2019.pdf#page=301| Source]])
> Suppose $f$ and $g$ are differentiable on an open interval $I$ containing $a$ with $g'(x)\neq 0$ on $I$ when $x \neq a$. If $$\lim_{ x \to a }f(x) = \lim_{ x \to a }g(x)=0$$, then
> $$\lim_{ x \to a } \frac{f(x)}{g(x)}= \lim_{ x \to a } \frac{f'(x)}{g'(x)}$$
> provided the limit on the right exists (or is $\pm \infty$). The rule also applies if $x \to a$ is replaced with $x \to \pm \infty$, $x \to a^+$ or $x \to a^-$
>>[!proof]-
>>We prove the special case that $f'$ and $g'$ are continuous at $a$ and $f(a)=g(a)=0$ and $g'(a)\neq 0$
>>$$\begin{align}
>> \lim_{ x \to a } \frac{f'(x)}{g'(x)} &= \frac{f'(a)}{g'(a)} \\
>> &=  \frac{\lim\limits_{ x \to a }\frac{f(x)-f(a)}{x-a}}{\lim\limits_{ x \to a }\frac{g(x)-g(a)}{x-a}} \\
>> &= \lim_{ x \to a } \frac{\frac{f(x)-f(a)}{x-a}}{\frac{g(x)-g(a)}{x-a}} \\
>> &= \lim_{ x \to a } {\frac{f(x)-f(a)}{\cancel{ x-a }}}{\frac{\cancel{ x-a }}{g(x)-g(a)}} \\
>> &= \lim_{ x \to a } {\frac{f(x)-f(a)}{g(x)-g(a)}} \\ 
>> &= \lim_{ x \to a } \frac{f(x)}{g(x)}\tag{$f(a)=g(a)=0$}
>>\end{align}$$
>>$$\tag*{$\square$}$$

^eec6b8

