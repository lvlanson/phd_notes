>[!def] Definition Inner Product ([[../../../PDFs/howell2016.pdf#page=141|Source]])
>Let $f,g$ be two piecewise continuous functions defined on the interval $(\alpha, \beta)$. The **inner product** of $f$ with $g$ is denoted by $\langle f,g \rangle$ and defined by
>$$\langle f,g \rangle = \int _{\alpha}^\beta f(t)g^*(t) \, dt $$
> where $g^*(t)$ denotes the [[../Complex Analysis/Fundamental Properties|complex conjugate]] of $g(t)$. If $g$ is real-valued, then $g^*=g$

^e3ca10

>[!theorem] Theorem Properties of the Inner Product ([[../../../PDFs/howell2016.pdf#page=142|Source]])
> Suppose $a,b \in \mathbb{K}$ and $f,g,h$ are piecewise continuous functions on the finite interval $(\alpha,\beta)$, then
> $$\begin{alignat}{2}
> (i)\quad& \langle af+bg\,,\, h\rangle &&=  a \langle f\,,\,h \rangle + b \langle g\,,\,h \rangle \\
> (ii)\quad & \langle f\,,\,ag + bh \rangle &&= a^*\langle f\,,\,g \rangle + b^*\langle g\,,\,h \rangle \\
> (iii)\quad & \langle g\,,\,f \rangle &&= \langle f\,,\,g \rangle^* \\
> (iv)\quad & \langle f\,,\,f \rangle\geq 0 &&\text{ with } \langle f \,,\,f \rangle \Longleftrightarrow f\Big|_{(\alpha,\beta)} \equiv 0
>\end{alignat}$$

>[!def] Definition Norm of a Function ([[../../../PDFs/howell2016.pdf#page=143|Source]])
>Let $f$ be a piecewise continuous function, then the norm of $f$ denoted by $\lvert\lvert f \rvert\rvert$ is defined as
>$$\lvert\lvert f \rvert\rvert = \sqrt{ \langle f\,,\,f \rangle } $$
>>[!note]
>>This norm is equivalent to the $L^2[\alpha,\beta]$ norm, which can also be found in [[../../../PDFs/olson2017.pdf#page=45|Olson (2017)]]

^7c5e1e

>[!def] Definition Orthogonality ([[../../../PDFs/olson2017.pdf#page=46|Source 1]], [[../../../PDFs/howell2016.pdf#page=143|Source 2]])
>1. The functions $f,g \in L^2[a,b]$ are orthogonal if
>$$\langle f,g \rangle =0$$
>2. A collection or set of functions $\{ o_{k}(t) \}_{k=0}^N$ is orthogonal if
>$$ \langle \phi_{j}, \phi_{i} \rangle= 0 \qquad \forall i\neq j$$
>3. A set of functions is orthonormal if they are orthogonal and $\lvert\lvert \phi_{j} \rvert\rvert = 1$
> These can be normalized using $\psi_{j}=\frac{\phi_{j}}{\lvert\lvert \phi_{j} \rvert\rvert}$

>[!theorem] Theorem Orthogonality of Sine and Cosine Functions ([[../../../PDFs/olson2017.pdf#page=46|Source]])
>The functions $\{ \cos(kt) \}_{k=0}^\infty$ and $\{ \sin(kt) \}_{k=0}^\infty$ are orthogonal on the interval $[-\pi,\pi]$, i.e.
>$$\begin{align}
> \int  \cos(mt)\sin(nt) \, dt &= 0 \\
> \int  \cos(mt)\cos(nt) \, dt &= 0 \qquad \text{ with }n\neq m\\
> \int  \sin(mt)\sin(nt) \, dt &= 0 \qquad \text{ with }n\neq m\\ 
>\end{align}$$
>>[!remark]-
>> The functions described by the [[#^93ee52| Generalized Fourier Transformation]] are also orthogonal on the corresponding interval $[a,b]$
>
>>[!proof]-
>>>[!recall] Trigonometric Addition Identities
>>>$$\begin{align}
>>> \sin(\alpha \pm \beta) &= \sin(\alpha)\sin(\beta) \pm \cos(\alpha)\cos(\beta) \\
>>> \cos(\alpha \pm \beta) &= \cos(\alpha)\cos(\beta) \mp \sin(\alpha)\sin(\beta)
>>>\end{align}$$
>>
>>>We will prove:
>>>1. all cosines and sines are orthogonal to each other
>>>2. all cosines are orthogonal to each other
>>>3. all sines are orthogonal to each other
>>
>>1.  Note, $\sin$ is even and $\cos$ is odd, hence $\sin \cdot \cos$  is odd too. By the [[#^e42703| definition of even and odd functions]] we know, that 
>>$$\int _{-\pi}^\pi \cos(mt)\sin(nt) \, dt =0 $$
>>regardless of $m$ and $n$
>>2. We want to show that
>> $$\int _{-\pi}^\pi \cos(mt)\cos(nt) \, dt =0 \qquad \text{ with } m \neq n$$
>>Note, the following identities hold
>>$$\begin{align}
>> \cos(mt+nt) &= \cos(mt)\cos(nt)-\sin(mt)\sin(nt) \tag{1} \\
>> \cos(mt-nt) &= \cos(mt)\cos(nt)+\sin(mt)\sin(nt) \tag{2}
>>\end{align}$$
>>Adding these terms yield
>>$$\begin{align}
>> \cos(mt+nt)+\cos(mt-nt) &= \cos(mt)\cos(nt)\cancel{ -\sin(mt)\sin(nt) }( +  \cos(mt)\cos(nt)+\cancel{ \sin(mt)\sin(nt) } \\
>> &= 2\cos(mt)\cos(nt)
>>\end{align}$$
>>Dividing by two gives the expression under the integral
>>$$\cos(mt)\cos(nt) = \frac{1}{2} (\cos(mt+nt)+\cos(mt-nt))$$
>>Hence, we can substitute under the integral and get
>>$$\begin{align}
>> \int _{-\pi}^\pi \cos(mt)\cos(nt) \, dt &= \frac{1}{2}\int _{-\pi}^\pi   \cos(mt+nt)+\cos(mt-nt) \, dt \\
>> &= \frac{1}{2} \left[\frac{\sin((m+n)t)}{m+n} + \frac{\sin((m-n)t)}{m-n}\right]_{-\pi}^\pi \\
>>\end{align}$$
>>Since $m,n \in \mathbb{N}$ we know that $\sin(k\pi) = 0$ for any $k = n+m$ with $n \neq m$, hence
>>$$ \int _{-\pi}^\pi \cos(mt)\cos(nt) \, dt = 0$$
>>3. We want to show that
>> $$\int _{-\pi}^\pi \sin(mt)\sin(nt) \, dt = 0 \qquad\text{ with } m \neq n$$
>> Note, the following identities hold
>> $$\begin{align}
>> \cos(mt+nt) &= \cos(mt)\cos(nt)-\sin(mt)\sin(nt) \tag{1} \\
>> \cos(mt-nt) &= \cos(mt)\cos(nt)+\sin(mt)\sin(nt) \tag{2}
>>\end{align}$$
>>Subtracting these terms yield
>>$$\begin{align}
>> \cos(mt+nt) - \cos(mt-nt) &= \cancel{ \cos(mt)\cos(nt) }-\sin(mt)\sin(nt)\cancel{  -\cos(mt)\cos(nt) }-\sin(mt)\sin(nt)\\ \\
>> &= -2\sin(mt)\sin(nt)
>>\end{align} $$
>>Dividing by minus two gives the expression under the integral
>>$$\begin{align}
>> -\frac{1}{2}(\cos(mt+nt) - \cos(mt-nt)) &= \sin(mt)\sin(nt)
>>\end{align}$$
>>We substitute this and get the same expression as in case 2. except the factor in front of the integral is negative, i.e.
>>$$\int _{-\pi}^\pi \sin(mt)\sin(nt) \, dt = -\frac{1}{2}\int _{-\pi}^\pi   \cos(mt+nt)+\cos(mt-nt) \, dt $$
>>Hence, the conclusion is the same as in case 2, i.e. for $m,n \in \mathbb{N}$ we know that $\sin(k\pi) = 0$ for any $k = n+m$ with $n \neq m$, hence
>>$$\int _{-\pi}^\pi \sin(mt)\sin(nt) \, dt = 0 \tag*{$\square$}$$
>
>>[!note]- The case $m=n$
>>If $m=n$ we have
>>$$\begin{align}
>> \int _{-\pi}^\pi \cos(nt)\cos(nt) \, dt &= \int _{-\pi}^\pi   \cos^2(nt) \, dt \\
>>  &= 2\int _{0}^\pi   \cos^2(nt) \, dt \tag{$\cos$ even function}\\
>>  &= 2\left[\frac{1}{2}(\cos(t)\sin(t) + t)\right]_{0}^\pi \, \\
>>  &= \cos(\pi)\sin(\pi) + \pi - \underbrace{ (\cos(0)\sin(0)) }_{ =0 } \,  \\
>>  &= (-1)\cdot0 + \pi \,  \\
>>  &= \pi \,  \\
>>\end{align}$$
>>Similarly, for the $\sin$ part we have
>>$$\begin{align}
>>\int_{-\pi}^\pi \sin(nt)\sin(nt) \, dt &= \int_{-\pi}^\pi \sin^2(nt) \, dt \\
>>&= \int_{-\pi}^\pi \frac{1 - \cos(2nt)}{2} \, dt \\
>>&= \frac{1}{2} \int_{-\pi}^\pi (1 - \cos(2nt)) \, dt \\
>>&= \frac{1}{2} \left[t - \frac{\sin(2nt)}{2n}\right]_{-\pi}^\pi \\
>>&= \frac{1}{2} \left(\pi - (-\pi) - \frac{\sin(2n\pi)}{2n} + \frac{\sin(-2n\pi)}{2n}\right) \\
>>&= \frac{1}{2} \left(2\pi + \frac{\sin(2n\pi)}{2n} - \frac{\sin(2n\pi)}{2n}\right) \\
>>&= \pi
>>\end{align}$$
>
>>[!note]- The case $m=n=0$
>>If $m=n=0$ we have
>>$$\begin{align}
>>\int _{-\pi}^\pi \cos(0)\cos(0) \, dt &= \int _{-\pi}^\pi   1 \, dt \\
>> &= [t]_{-\pi}^\pi \\
>> &= 2\pi
>>\end{align}$$
>>and
>>$$\begin{align}
>>\int _{-\pi}^\pi \sin(0)\sin(0) \, dt &= \int _{-\pi}^\pi   0 \, dt \\
>> &= 0 \\
>> &= 0
>>\end{align}$$

^31a727

## Orthogonal Function Expansions

>[!theorem] Theorem on Orthogonal Expansions 
>Let $\{ \phi_{k} \}_{k=1}^\infty$ be an orthogonal set of functions on an interval $(\alpha, \beta)$, and let $f$ be a function on $(\alpha,\beta)$. If $f$ can be represented as a (possibly infinite) linear combination of $\phi_{k}$'s, i.e. there are constants $c_{1}, c_{2}, c_{3}, \dots$ such that
>$$f(t)= \sum_{k}c_{k}\phi_{k}(t) \quad \text{ on } (\alpha,\beta)$$
>then, for each $k$,
>$$c_{k} = \frac{\left\langle f\,,\,\phi_{k} \right\rangle}{\lvert\lvert \phi_{k} \rvert\rvert^2 } $$

^3f9bbe

>[!theorem] Theorem Cauchy-Schwarz Inequality for Inner Products ([[../../../PDFs/howell2016.pdf#page=147|Source]])
>Let $f$ and $g$ be two piecewise continuous functions on the finite interval $(\alpha, \beta)$. Then
>$$\lvert \langle f\,,\,g \rangle \rvert \leq \lvert\lvert f \rvert\rvert \; \lvert\lvert g \rvert\rvert $$
>>[!proof]-
>>First rewrite 
>>$$\begin{align}
>> \lvert \langle f\,,\,g \rangle \rvert \leq \lvert\lvert f \rvert\rvert \; \lvert\lvert g \rvert\rvert \quad &\Longleftrightarrow \quad\left| \int_{\alpha}^\beta f(t)g^*(t) \, dt\right|\leq  \sqrt{ \int _{\alpha}^\beta f(t)f^*(t) \, dt  }\;\sqrt{ \int _{\alpha}^\beta g(t)g^*(t) \, dt  } \\
>>  &\Longleftrightarrow  \quad\left| \int_{\alpha}^\beta f(t)g^*(t) \, dt\right|\leq  \sqrt{ \int _{\alpha}^\beta \lvert f(t) \rvert^2  \, dt  }\;\sqrt{ \int _{\alpha}^\beta \lvert g(t) \rvert^2  \, dt  }
>>\end{align} $$
>>The LHS of the inequality can be rewritten using the [[../Calculus/Integration#^a5bf98|absolute value integral theorem]] as follows
>>$$\begin{align}
>> \left| \int_{\alpha}^\beta f(t)g^*(t) \, dt\right| \leq \int _{\alpha}^\beta \lvert f(t)g^*(t) \rvert  \, dt = \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert   \, dt  
>>\end{align}$$
>>Hence, it is sufficient to show
>>$$\int _{\alpha}^\beta \lvert f(t) \rvert\; \lvert g(t) \rvert   \, dt \leq \sqrt{ \int _{\alpha}^\beta \lvert f(t) \rvert^2  \, dt  }\;\sqrt{ \int _{\alpha}^\beta \lvert g(t) \rvert^2  \, dt  } $$
>> 1. Case: $f \equiv 0$ or $g \equiv 0$
>>> We get by definition
>>> $$\int _{\alpha}^\beta f(t)\, dt = 0 \quad\text{ or }\quad\int _{\alpha}^\beta g(t)\, dt = 0$$
>>> and as immediate consequence
>>> $$\begin{align}
>>> \int _{\alpha}^\beta \lvert f(t) \rvert\; \lvert g(t) \rvert   \, dt &\leq \sqrt{ \int _{\alpha}^\beta \lvert f(t) \rvert^2  \, dt  }\;\sqrt{ \int _{\alpha}^\beta \lvert g(t) \rvert^2  \, dt  } \\
>> 0 & \leq 0 \tag*{$\checkmark$}
>>>\end{align}$$
>>
>>2. Case: $f,g \not\equiv 0$
>>> Denote
>>> $$A= \lvert\lvert f \rvert\rvert \quad \text{ and } \quad B= \lvert\lvert g \rvert\rvert $$
>>>Then we can explicitly state
>>>$$A^2= \int _{\alpha}^\beta \lvert f \rvert^2  \, dt  \quad \text{ and } \quad B^2= \int _{\alpha}^\beta \lvert g \rvert^2  \, dt $$
>>>and since the square is always non-negative, we can confidently state
>>>$$0 \leq (B \lvert f(t) \rvert - A| g(t) | )^2$$
>>>>[!note]
>>>>We use this statement, since it is true, to show that the Cauchy-Schwarz inequality is true as well
>>>
>>>Using simple algebra we get
>>>$$\begin{align}
>>> 0 &\leq \int _{\alpha}^\beta \Big(B \lvert f(t) \rvert - A\lvert g(t) \rvert  \Big)^2 \, dt \tag{1} \\
>>>   &= \int _{\alpha}^\beta \Big[B^2 \lvert f(t) \rvert^2 - 2AB \lvert f(t) \rvert\, \lvert g(t) \rvert + A^2 \lvert g(t) \rvert^2    \Big]\, dt \tag{Binomial Expansion} \\
>>>   &=B^2 \underbrace{ \int_{\alpha}^\beta \lvert f(t) \rvert^2  \, dt }_{ =A^2 } - 2AB \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert  \, dt + A^2 \underbrace{ \int _{\alpha}^\beta \lvert g(t) \rvert^2 \, dt }_{ =B^2 } \tag{Linearity} \\ 
>>>   &= B^2A^2 - 2AB \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert  \, dt  + A^2B^2 \\
>>>   &= 2AB \left[AB - \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert   \, dt \right] \\
>>>\end{align}$$
>>>We now use this result on equation $(1)$
>>>$$\begin{alignat}{2}
>>> 0  &\leq 2AB \left[AB - \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert   \, dt \right] \qquad&&\Big\vert :2AB \\
>>> 0 &\leq AB - \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert   \, dt \qquad&&\Big\vert + \int (\dots) \, dt  \\
>>> \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert   \, dt  &\leq AB
>>>\end{alignat}$$
>>>Note the construction of $A$ and $B$ gives $AB$
>>>$$\begin{align}
>>> \int _{\alpha}^\beta \lvert f(t) \rvert \; \lvert g(t) \rvert &\leq \sqrt{ \int _{\alpha}^\beta \lvert f(t) \rvert^2  \, dt  }\;\sqrt{ \int _{\alpha}^\beta \lvert g(t) \rvert^2  \, dt  }  \\
>>> \lvert \langle f\,,\,g \rangle \rvert&\leq \lvert\lvert f \rvert\rvert \, \lvert\lvert g \rvert\rvert  \tag*{$\checkmark$}
>>>\end{align} $$ 
>>
>>$$\tag*{$\square$}$$

^e14b2d

>[!lemma] Lemma Bessel's Inequality (Part 1) ([[../../../PDFs/howell2016.pdf#page=149|Source]])
> Assume $\{ \phi_{1},\dots,\phi_{N} \}$ is a finite orthogonal set of piecewise continuous functions on a finite interval $(\alpha, \beta)$, and let $f$ be any piecewise continuous function on $(\alpha, \beta)$. For $k=1,2,\dots , N$, let $c_{k}$ be the corresponding generalized Fourier coefficient,
> $$c_{k} = \frac{\langle f\,,\,\phi_{k} \rangle}{\lvert\lvert \phi_{k} \rvert\rvert^2 }$$
> Then
> $$\left\lvert \left\lvert  f - \sum_{k=1}^N c_{k}\phi_{k}  \right\rvert \right\rvert^2 = \lvert\lvert f \rvert\rvert^2 - \sum_{k=1}^N \lvert c_{k} \rvert^2 \, \lvert\lvert \phi_{k} \rvert\rvert^2    $$
>>[!proof]-
>>First, we denote as shorthand 
>>$$S_{n} = \sum_{k=1}^N c_{k}\phi_{k}(t)$$
>> We compute 
>> $$\begin{align}
>> \left\lvert \left\lvert  f - \sum_{k=1}^N c_{k} \phi_{k}  \right\rvert \right\rvert^2 &= \lvert\lvert f - S_{N} \rvert\rvert^2 \\
>>  &= \langle f - S_{N}\,,\, f-S_{N} \rangle   \\
>>  &= \left\langle f\,,\,f \right\rangle - \left\langle f \,,\,S_{N} \right\rangle - \left\langle S_{N}\,,\,f \right\rangle + \left\langle S_{N}\,,\,S_{N} \right\rangle \tag{1} \\
>>\end{align}$$
>>We will identify each of the terms
>>$$\begin{align}
>> \left\langle f\,,\,f \right\rangle &= \lvert\lvert f \rvert\rvert^2 \tag{2} \\
>>  \left\langle f\,,\,S_{N} \right\rangle &= \left\langle f\,,\, \sum_{k=1}^N c_{k} \phi_{k} \right\rangle  \\
>> &= \sum_{k=1}^N c_{k}^* \left\langle f\,,\,\phi_{k} \right\rangle  \\
>> &= \sum_{k=1}^N c_{k}^*  \left(c_{k} \lvert\lvert \phi_{k} \rvert\rvert^2\right) \\
>> &=\sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2 \tag{3} \\
>> \left\langle S_{N}\,,\,f \right\rangle &= \left\langle f\,,\,S_{N} \right\rangle^* \\
>> &= \left(\sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2\right)^* \\
>> &= \sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2 \tag{4}\\
>>\left\langle S_{N}\,,\,S_{N} \right\rangle &= \left\langle \sum_{k=1}^N c_{k} \phi_{k}\,,\, \sum_{n=1}^N c_{n} \phi_{n} \right\rangle \\ 
>>    &= \sum_{k=1}^N c_{k}\left\langle  \phi_{k}\,,\, \sum_{n=1}^N c_{n} \phi_{n} \right\rangle \\
>> &=  \sum_{k=1}^N c_{k}\left( \sum_{n=1}^N c_{n}^* \left\langle \phi_{k}\,,\,\phi_{n} \right\rangle \right) \\
>> &=  \sum_{k=1}^N c_{k}\left( \sum_{n=1}^N c_{n}^* \begin{Bmatrix}
>> \lvert\lvert c_{k} \rvert\rvert^2 & \text{ if } n=k \\
>> 0 & else
>>\end{Bmatrix} \right) \\
>> &=\sum_{k=1}^N \,\lvert c_{k} \rvert \,\lvert\lvert c_{k} \rvert\rvert ^2 \tag{5}
>>\end{align}$$
>>>[!note] Notes on Result $(3)$ and $(5)$
>>>For equation $(3)$ we used
>>>$$\begin{align}
>>> c_{k} &= \frac{\langle f\,,\,\phi_{k} \rangle}{\lvert\lvert \phi_{k} \rvert\rvert^2 } \\
>>> \langle f\,,\,\phi_{k} \rangle &= c_{k} \lvert\lvert \phi_{k} \rvert\rvert^2
>>>\end{align}$$
>>>For equation $(5)$ we used the properties of the inner product
>>
>>Inserting these results back into equation $(1)$
>>$$\begin{align}
>>\left\lvert \left\lvert  f - \sum_{k=1}^N c_{k}\phi_{k}  \right\rvert \right\rvert^2 &= \lvert\lvert f \rvert\rvert^2 - \sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2 - \sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2 + \sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2 \\
>>  &=  \lvert\lvert f \rvert\rvert^2 + \sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2 \tag*{$\square$}
>>\end{align}$$

^a7eff2

>[!theorem] Theorem Bessel's Inequality (Part 2) ([[../../../PDFs/howell2016.pdf#page=151|Source]])
> Assume that $\{ \phi_{1}, \phi_{2},\dots \}$ is an infinite, orthogonal set of piecewise continuous functions on a finite interval $(\alpha, \beta)$. Let $f$ be any piecewise continuous function on $(\alpha, \beta)$, and, for each positive integer $k$, let $c_{k}$ be the corresponding generalized Fourier coefficient,
> $$c_{k} = \frac{\left\langle f\,,\,\phi_{k} \right\rangle }{\lvert\lvert \phi_{k} \rvert\rvert^2}$$
> Then
> $$\sum_{k=1}^N \lvert c_{k} \rvert^2 \lvert\lvert \phi_{k} \rvert\rvert^2 \leq \lvert\lvert f \rvert\rvert^2 $$
> for every positive integer $N$. Moreover, the infinite series $\sum_{k=1}^\infty \lvert c_{k} \rvert^2 \lvert\lvert \phi_{k} \rvert\rvert^2$ converges and
> $$\sum_{k=1}^\infty \lvert c_{k} \rvert ^2 \lvert\lvert \phi_{k} \rvert\rvert ^2 \leq \lvert\lvert f \rvert\rvert ^2$$
>>[!proof]-
>> Let $N$ be any positive integer. We use the identity given by [[#^a7eff2| Bessel's inequality (Part 1)]], i.e.
>> $$\begin{alignat}{2}
>> 0 &\leq \left\lvert \left\lvert  f - \sum_{k=1}^N c_{k}\phi_{k}  \right\rvert \right\rvert^2 = \lvert\lvert f \rvert\rvert^2 - \sum_{k=1}^N \lvert c_{k} \rvert^2  \lvert\lvert \phi_{k} \rvert\rvert^2   \qquad&&\\
>> 0 &\leq \lvert\lvert f \rvert\rvert^2 - \sum_{k=1}^N \lvert c_{k} \rvert^2\lvert\lvert \phi_{k} \rvert\rvert^2 \qquad&&\Big\vert +\sum_{k=1}^N \lvert c_{k} \rvert^2\lvert\lvert \phi_{k} \rvert\rvert^2 \\
>> \sum_{k=1}^N \lvert c_{k} \rvert^2\lvert\lvert \phi_{k} \rvert\rvert^2 &\leq \lvert\lvert f \rvert\rvert ^2 \tag*{$\checkmark$}
>>\end{alignat}$$
>>This proves the first part of the theorem. For the second part we need to use the [[../Calculus/Series#^6499f9|bounded partial sums theorem]], such that we can state
>>$$\sum_{k=1}^\infty \lvert c_{k} \rvert^2\lvert\lvert \phi_{k} \rvert\rvert^2 = \lim_{ n \to \infty } \sum_{k=1}^N \lvert c_{k} \rvert^2\lvert\lvert \phi_{k} \rvert\rvert^2 \leq \lvert\lvert f \rvert\rvert ^2\tag*{$\square$} $$

^5b7f44

>[!example] Example Fourier Series and Bessel's Inequality ([[../../../PDFs/howell2016.pdf#page=151|Source]])
>Let $f$ be any periodic, piecewise continuous function with period $p$, then we have the Fourier series
>$$\mathcal{F}[f]|_{t} = A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) + b_{k}\sin(2\pi \omega_{k}t)\Big]$$
>with $\omega_{k}=\frac{k}{p}$
>>[!note] Note Orthogonal Set
>>The set of trigonometric Fourier coefficients is an orthogonal set by the [[#^31a727| sine and cosine orthogonality theorem]] over the interval of length $p$
>>$$\{ \underbrace{ 0 }_{ =\sin(0) }, \underbrace{ 1 }_{ =\cos(0) },\; \cos(2\pi \omega_{1}t),\; \sin(2\pi \omega_{1}t),\;\cos(2\pi \omega_{2}t),\; \sin(2\pi \omega_{2}t),\dots \}$$
>
>Then we can state the series as
>$$\begin{align}
> &\lvert A_{0} \rvert^2 \lvert\lvert 1 \rvert\rvert^2 + \sum_{k=1}^\infty \Big[\lvert a_{k} \rvert^2 \; \lvert\lvert \cos(2\pi \omega_{k}t) \rvert\rvert^2 + \lvert b_{k} \rvert^2 \; \lvert\lvert \sin(2\pi \omega_{k}t) \rvert\rvert^2    \Big]    \\
> =\,& \lvert A_{0} \rvert^2 p^2+ \sum_{k=1}\left[\lvert a_{k} \rvert^2\frac{p^2}{4} + \lvert b_{k} \rvert^2 \frac{p^2}{4}  \right]
>\end{align} $$
>>[!note]- Computation the Norms
>>We are relying on the [[../Trigonometry/Trigonometric Identities#^82bd09|trigonometric identities]]
>>1. Computing $\lvert\lvert \cos(2\pi \omega_{k}t) \rvert\rvert^2$
>>First, computing the unsquared norm
>> $$\begin{align}
>> \lvert\lvert \cos(2\pi \omega_{k}t) \rvert\rvert &= \Big\langle \cos(2\pi \omega_{k}t)\,,\, \cos(2\pi \omega_{k}t)\Big\rangle   \\
>>   &= \int _{0}^p \lvert \cos(2\pi \omega_{k}t) \rvert^2  \, dt  \\
>>   &= \int _{0}^p \cos^2(2\pi \omega_{k}t) \, dt \\
>>   &= \int _{0}^p \frac{1+\cos(4\pi \omega_{k}t)}{2} \, dt \\
>>   &= \int _{0}^p  \frac{1}{2} \, dt + \frac{1}{2}\int _{0}^p \cos(4\pi \omega_{k}t) \, dt \\ 
>>   &= \left[\frac{1}{2}t\right]_{0}^p + \frac{1}{2}\left[ \frac{1}{4\pi \omega_{k}}\sin(4\pi \omega_{k}t)\right]_{0}^p  \tag*{$\left(\omega_{k}= \frac{k}{p}\right)$} \\
>>   &= \left[\frac{1}{2}t\right]_{0}^p + \frac{1}{2}\left[\frac{p}{4\pi k}\sin\left( \frac{4\pi k}{p}t\right)\right]_{0}^p \tag{$k>0$}\\
>>   &= \frac{1}{2}p + \frac{1}{2}\left(\frac{p}{4\pi k}\underbrace{ \sin(4\pi k) }_{ =0 } - \frac{p}{4\pi k}\underbrace{ \sin(0) }_{ =0 }\right) \\
>>   &= \frac{1}{2}p 
>>\end{align}$$
>>Now taking the square
>>$$\begin{align}
>> \lvert\lvert \cos(2\pi \omega_{k}t) \rvert\rvert^2 &= \left( \frac{p}{2} \right)^2  \\
>> &= \frac{p^2}{4} \tag*{$\checkmark$}
>>\end{align}$$
>>2. Computing $\lvert\lvert \sin(2\pi \omega_{k}t) \rvert\rvert^2$
>> Again, computing the non-squared norm first
>> $$\begin{align}
>> \lvert\lvert \sin(2\pi \omega_{k}t) \rvert\rvert &= \Big\langle \sin(2\pi \omega_{k}t)\,,\, \sin(2\pi \omega_{k}t)\Big\rangle   \\
>>   &= \int _{0}^p \lvert \sin(2\pi \omega_{k}t) \rvert^2  \, dt  \\
>>   &= \int _{0}^p \sin^2(2\pi \omega_{k}t) \, dt \\ 
>>   &=\int _{0}^p \frac{1 - \cos(4\pi \omega_{k}t) \,}{2} dt \\
>>   &= \int _{0}^p  \frac{1}{2} \, dt - \underbrace{ \frac{1}{2}\int _{0}^p \cos(4\pi \omega_{k}t) \, dt }_{ =0 } \\
>>  &= \frac{1}{2}p 
>>\end{align}$$
>>Squaring this result gives again
>>$$\begin{align}
>> \lvert\lvert \sin(2\pi \omega_{k}t) \rvert\rvert^2 &= \frac{p^2}{4} \tag*{$\checkmark$}
>>\end{align}$$
>>3. Computing $\lvert\lvert 1 \rvert\rvert^2$
>>$$\begin{align}
>> \lvert\lvert 1 \rvert\rvert &= \left\langle 1\,,\,1 \right\rangle  \\
>> &= \int _{0}^p 1^2 \, dt \\
>> &= p 
>>\end{align}$$
>> Squaring the result yields 
>> $$\lvert\lvert 1 \rvert\rvert^2 = p^2 \tag*{$\checkmark$}$$
>
> By [[#^5b7f44| Bessel's inequality]] we know
> $$\lvert A_{0} \rvert^2 p^2+ \sum_{k=1}\left[\lvert a_{k} \rvert^2\frac{p^2}{4} + \lvert b_{k} \rvert^2 \frac{p^2}{4}  \right] \leq \lvert\lvert f \rvert\rvert^2 $$
>>[!note]
>> The terms of the series must approach $0$ as $k \to \infty$, since the series is bounded by $\lvert\lvert f \rvert\rvert^2$, i.e.
>> $$\begin{align}
>> \lim_{ k \to \infty } \lvert a_{k} \rvert^2 \frac{p^2}{4} &= 0  \\
>> \lim_{ k \to \infty } \lvert b_{k} \rvert^2 \frac{p^2}{4} &= 0 
>>\end{align}$$
>
>>[!note] Note on the Convergence of the Fourier Series
>>Note, that this result does not give us the guarantee of convergence of the Fourier series
>>$$A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) + b_{k} \sin(2\pi \omega_{k}t)\Big]$$

>[!theorem] Theorem General Riemann-Lebgesgue Lemma ([[../../../PDFs/howell2016.pdf#page=152|Source]])
>Let $f$ be any piecewise continuous function on a finite interval $(\alpha, \beta)$ and let $\{ \phi_{1}, \phi_{2}, \dots \}$ be any infinite orthogonal set of piecewise continuous functions on $(\alpha, \beta)$. Assume that, for some finite constant $C$ and every positive integer $k$,
>$$\lvert\lvert \phi_{k} \rvert\rvert < C$$
>then
>$$\lim_{ k \to \infty } \int _{\alpha}^\beta f(t)\phi_{k}^*(t) \, dt =0 $$