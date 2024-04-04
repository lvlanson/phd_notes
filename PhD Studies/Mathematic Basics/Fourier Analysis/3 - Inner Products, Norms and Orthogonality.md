>[!def] Definition Inner Product ([[../../../PDFs/howell2016.pdf#page=141|Source]])
>Let $f,g$ be two piecewise continuous functions defined on the interval $(\alpha, \beta)$. The **inner product** of $f$ with $g$ is denoted by $\langle f,g \rangle$ and defined by
>$$\langle f,g \rangle = \int _{\alpha}^\beta f(t)g^*(t) \, dt $$
> where $g^*(t)$ denotes the [[../Complex Analysis/Fundamental Properties|complex conjugate]] of $g(t)$. If $g$ is real-valued, then $g^*=g$

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

>[!theorem] Theorem Cauchy-Schwarz Inequality for Inner Products ([[../../../PDFs/howell2016.pdf#page=147|Source]])
>Let $f$ and $g$ be two piecewise continuous functions on the finite interval $(\alpha, \beta)$. Then
>$$\lvert \langle f\,,\,g \rangle \rvert \leq \lvert\lvert f \rvert\rvert \; \lvert\lvert g \rvert\rvert $$
>>[!proof]
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

## Orthogonal Function Expansions

