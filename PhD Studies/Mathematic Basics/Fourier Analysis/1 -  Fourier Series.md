>[!def] Definition $L^2[a,b]$ Space ([[../../../Sources/olson2017.pdf#page=33|Source]])
>The set of functions $$f(t):[a,b] \to \mathbb{R}$$ whose squared integral is finite, i.e.
>$$\int _{a}^b \lvert f(t) \rvert^2  \, dt < \infty $$
>is referred to as 
>$$L^2[a,b]$$
>or the square integrable functions on $[a,b]$

>[!note]
>$L^2[a,b]$ is a [[../Functional Analysis/Functional Analysis Basics#^b3bce8|normed vector space]] with $f \in L^2$
>$$\lvert\lvert f \rvert\rvert_{2} = \int_{a}^b \lvert f(t) \rvert^2  \, d\mu (t)  $$

>[!property] $L^2[a,b]$ being a vector space
>The space of square integrable functions on $[a,b]$ forms a vector space (both for $\mathbb{R}$ and $\mathbb{C})$
>>[!proof]-
>>Let $f,g \in L^2[a,b]$
>> $$\begin{align}
>> \lvert\lvert c_{1}f+c_{2}g \rvert\rvert^2_{2} &= \int _{a}^b(c_{1}f + c_{2} g)^2 \, dt  \\
>>     &=\int _{a}^bc_{1}^2f^2 + c_{2}^2 g^2 +  2c_{1}c_{2}fg \, dt \\
>>     &=c_{1}^2\underbrace{ \int _{a}^bf^2 \, dt }_{ < \infty } + c_{2}^2\underbrace{ \int_{a}^b  g^2 \, dt }_{ <\infty } +  2c_{1}c_{2} \int _{a}^b fg \, dt
>>\end{align} $$
>>The first two terms are finite, because the square of two finite values must be squared. For the last term we use the [[../Functional Analysis/Functional Analysis Basics#^8d565e|Cauchy-Schwartz Inequality]]
>>$$\left\lvert  \int _{a}^b fg \, dt   \right\rvert \leq \underbrace{ \lvert\lvert f \rvert\rvert^2_{2} \; \lvert\lvert g \rvert\rvert^2_{2} }_{ < \infty }   \tag*{$\square$}$$

>[!theorem] Theorem Fourier Transformation ([[../../../Sources/olson2017.pdf#page=34|Source]])
>Let $f \in L^2[-\pi, \pi ]$, then $f$ can be represented as
>$$f(t) = \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos(kt)+b_{k} \sin(kt)$$
>with
>$$\begin{align}
> a_{k} &= \frac{1}{\pi}\int _{-\pi}^\pi f(t)\cos(kt) \, dt \\
> b_{k} &= \frac{1}{\pi}\int _{-\pi}^\pi f(t)\sin(kt) \, dt 
>\end{align}$$

^da9999

>[!theorem] Theorem Generalized Fourier Transformation ([[../../../Sources/olson2017.pdf#page=34|Source]])
>Let $f \in L^2[-\pi, \pi ]$, then $f$ can be represented as
>$$f(t) = \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos\left( \frac{k\pi(t-h)}{H} \right)+b_{k} \sin(\frac{k\pi(t-h)}{H})$$
>with 
>$$\begin{align}
> a_{k} &= \frac{1}{H}\int _{a}^b f(t) \cos\left(\frac{k\pi(t-h)}{H} \right) \, dt \\
> b_{k} &= \frac{1}{H}\int _{a}^b f(t)\sin\left(\frac{k\pi(t-h)}{H} \right) \, dt 
>\end{align}$$
>and 
>$$\begin{align}
> H &= \frac{b-a}{2} \\
> h &= \frac{a+b}{2}
>\end{align}$$

^93ee52


>[!Remark]
>Setting $a=-\pi$ and $b=\pi$ in the [[#^93ee52|Generalized Fourier Transformation]] yields the [[#^da9999| Fourier Transformation]].

>[!property] Corollary
>Let $f \in L^2[-T, T]$, then $f$ can be represented as
>$$f(t)=\frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos\left( \frac{k\pi t}{T} \right) + b_{k} \sin\left( \frac{k\pi t}{T} \right)$$
>with 
>$$\begin{align}
> a_{k}&=\frac{1}{T} \int _{-T}^T f(t)\cos\left( \frac{k\pi t}{T} \right) \, dt \\
> b_{k}&= \frac{1}{T} \int _{-T}^T f(t)\sin\left( \frac{k\pi t}{T} \right) \, dt
>\end{align}$$

>[!def] Definition Even and Odd Functions ([[../../../Sources/olson2017.pdf#page=37|Source]])
>A function $f$ is said to be **even** if
>$$ f(t) = f(-t)$$
>A function $f$ is said to be **odd** if
>$$ f(t) = -f(-t)$$
>>[!example]
>> - $\cos(kt)$ is even
>> - $\sin(kt)$ is odd
>> - $t^k$ with $k \text{ mod } 2 = 0$ is even (monomial)
>> - $t^k$ with $k \text{ mod } 2 = 1$ is odd (monomial)
>>
>>>[!note]
>>> If $f$ is odd we have
>>> $$\int _{-T}^T f(t) \, dt = 0 $$

>[!property]
>The product of two functions being
>- even and even -> even
>- even and odd -> odd
>- odd and odd -> even

>[!def] Definition Characteristic Binary Function
>$$\begin{align}
>\mathcal{X}_a &= \begin{cases}
>1 & \text{ if } \lvert t \rvert< a \\
>0 & \text{ if } \lvert t \rvert > a
>\end{cases} \\
> \mathcal{X}_{[a,b]} &= \begin{cases}
> 1 & \text{ if } t \in \left[ a,b \right] \\
> 0 & \text{ if } t \not\in [a, b] 
>\end{cases}
>\end{align}$$