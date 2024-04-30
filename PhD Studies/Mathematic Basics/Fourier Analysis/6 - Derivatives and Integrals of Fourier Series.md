## Differentiation of Fourier Series

>[!lemma] Lemma Fourier Series of a Derivative ([[../../../PDFs/howell2016.pdf#page=207|Source]])
>Assume $f$ is a periodic, continuous, [[../Calculus/Differentiation#^680da2|piecewise smooth]] function with period $p$ and 
>$$\mathcal{F}[f]|_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i2\pi \omega_{k}t}$$
>then
>$$\begin{align}
> \mathcal{F}[f']|_t &= \sum_{k=-\infty}^\infty i2\pi \omega_{k}c_{k}e^{i2\pi \omega_{k}t} \\
> &= \frac{i 2\pi}{p}\sum_{k=-\infty}^\infty kc_{k}e^{i2\pi \omega_{k}t}
>\end{align}$$
>>[!proof]-
>>Let 
>>$$\begin{align}
>> \mathcal{F}[f]|_{t} &= \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}\\
>> \mathcal{F}[f']|_{t} &= \sum_{k=-\infty}^\infty d_{k}e^{i 2\pi \omega_{k}t}\\
>>\end{align}$$
>>with
>>$$\begin{align}
>> c_{k} &= \frac{1}{p}\int _{0}^p f(t)e^{-i 2\pi \omega_{k}t} \, dt  \\
>> d_{k} &= \frac{1}{p}\int _{0}^p f'(t)e^{-i 2\pi \omega_{k}t} \, dt  
>>\end{align}$$
>>Since $f$ is continuous we can use [[../Calculus/Integration#^thmIntByParts|integration by parts]] to solve $d_{k}$. We have
>>$$\begin{align}
>> \frac{dv}{dt} &= f' \\
>> v &= f  \\
>> u &=  e^{-i 2\pi \omega_{k}t} \\
>> \frac{du}{dt} &= -i2\pi \omega_{k}e^{-i 2\pi \omega_{k}t}
>>\end{align}$$
>>and get for the [[../Calculus/Integration#^thmIntByParts|integration by parts theorem]] $\int u\, dv \, = uv - \int v \,du$ 
>>$$\begin{align}
>> &\Big[f(t)e^{-i 2\pi \omega_{k}t}\Big]_{0}^p  - \int _{0}^p f(t)\Big[-i2\pi \omega_{k}e^{-i 2\pi \omega_{k}t}\Big] \, dt  \\
>> =& \Big(f(p)\underbrace{ e^{-i2\pi \omega_{k}p} }_{ p\omega_{k}=k } - f(0)e^{-2 \pi \omega _{k}0}\Big) +i2\pi \omega_{k} \underbrace{ \int _{0}^p f(t)e^{-i 2\pi \omega_{k}t} \, dt }_{ =c_{k} } \\
>> =&\underbrace{ \Big(\underbrace{ f(p) }_{ =f(0) }\underbrace{ e^{-i2\pi k} }_{ =e^0 }U - f(0)\Big) }_{ =0 }+ i2\pi \omega_{k}c_{k} \tag{$f$ periodic} \\
>> =& i2\pi \omega_{k}c_{k}
>>\end{align}$$
>>Therefore, we can conclude $$d_{k}= i2\pi \omega_{k}c_{k}$$ and finally 
>>$$\mathcal{F}[f']|_{t} = \sum_{k=-\infty}^\infty \underbrace{ i2\pi \omega_{k}c_{k} }_{ =d_{k} }e^{i 2\pi \omega_{k}t} \tag*{$\square$}$$
>

>[!theorem] Theorem Differentiation of Fourier Series ([[../../../PDFs/howell2016.pdf#page=207|Source]])
>Let $f$ be a periodic, continuous, [[../Calculus/Differentiation#^680da2|piecewise smooth]] function with period $p$ and
>$$\mathcal{F}[f]|_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i2\pi \omega_{k}t}$$
>If $f'$ is also piecewise smooth, then
>$$\sum_{k=-\infty}^\infty kc_{k}e^{i2\pi \omega_{k}t}$$
>converges for each $t$ at which $f'$ is continuous, and, as piecewise continuous functions
>$$\begin{align}
> f'(t)&= \sum_{k=-\infty}^\infty \frac{d}{dt}\Big[c_{k}e^{i2\pi \omega_{k}t}\Big] \\
> &= \frac{i 2\pi}{p}\sum_{k=-\infty}^\infty kc_{k}e^{i2\pi \omega_{k}t}
>\end{align}$$
>
>>[!proof]-
>> The proof follows from the [[5 - Fourier Convergence#^e8a98c|main theorem]] where $g(x)$ has a factor $k$ in it which does not invalidate the continuity property. Also note, since $f$ is piecewise smooth, its derivative is piecewise continuous.

^bbe431

>[!lemma] Lemma Trigonometric Fourier Series of a Derivative ([[../../../PDFs/howell2016.pdf#page=208|Source]])
> Assume $f$ is a periodic, continuous, [[../Calculus/Differentiation#^680da2|piecewise smooth]] smooth function with period $p$ and
> $$\mathcal{F}[f]|_{t}= A_{0}+ \sum_{k=1}^\infty a_{k}\cos(2 \pi \omega_{k}t) + b_{k}\sin(2 \pi \omega_{k}t)$$
> Then
> $$\begin{align}
> \mathcal{F}[f']|_{t} &= \sum_{k=1}^\infty -2\pi \omega_{k}a_{k}\cos(2 \pi \omega_{k}t) + 2\pi \omega_{k}b_{k}\sin(2 \pi \omega_{k}t)\\
> &= \frac{2\pi}{p}\sum_{k=1}^\infty - ka_{k}\cos(2 \pi \omega_{k}t) + kb_{k}\sin(2 \pi \omega_{k}t)
>\end{align}$$
>>[!proof] Proof Omitted -> Follows from the Exponential Fourier Series

>[!theorem] Theorem Differentiation of Trigonometric Fourier Series ([[../../../PDFs/howell2016.pdf#page=209|Source]])
>Let $f$ be a periodic, continuous, [[../Calculus/Differentiation#^680da2|piecewise smooth]] function with period $p$ and 
> $$\mathcal{F}[f]|_{t}= A_{0}+ \sum_{k=1}^\infty a_{k}\cos(2 \pi \omega_{k}t) + b_{k}\sin(2 \pi \omega_{k}t)$$
> converges for each $t$ at which $f'$ is continuous, and, as piecewise continuous functions
>$$\begin{align}
> f'(t)&=\sum_{k=1}^\infty -2\pi \omega_{k}a_{k}\cos(2 \pi \omega_{k}t) + 2\pi \omega_{k}b_{k}\sin(2 \pi \omega_{k}t)\\
> &= \frac{2\pi}{p}\sum_{k=1}^\infty - ka_{k}\cos(2 \pi \omega_{k}t) + kb_{k}\sin(2 \pi \omega_{k}t)
>\end{align}$$ 
>>[!proof] Proof Omitted -> Follows from the Exponential Fourier Series 

>[!property] Corollary Higher Order Differentiation of the Exponential Series ([[../../../PDFs/howell2016.pdf#page=209|Source]])
>Let $f$ be a periodic, continuous function with period $p$ and Fourier series
>$$\sum_{k=-\infty}^\infty c_{k}e^{i2\pi \omega_{k}t}$$
>Assume further that, for some positive integer $m$, $f$ is $(m-1)$-times differentiable, and $f^{(m-1)}$ is continuous and piecewise smooth, then
>$$\sum_{k=-\infty}^\infty k^m c_{k}e^{i2\pi \omega_{k}t}$$
>converges for each $t$ at which $f^{(m)}$ is continuous, and, as piecewise continuous functions,
>$$\begin{align}
> f^{(m)}&= \sum_{k=-\infty}^\infty d^m(dt^m)\Big[c_{k}e^{i 2\pi \omega_{k}t}\Big] \\
> &= \left( \frac{i2\pi}{p} \right)^m \sum_{k=-\infty}^\infty k^m c_{k}e^{i 2 \pi \omega_{k}t}
>\end{align}$$
>>[!proof]-
>>Note, the case for $m=1$ is the [[#^bbe431|theorem of differentiating Fourier series]] and is therefore already shown. Assume $m>1$, then $f'(t)$ is differentiable and [[../Calculus/Differentiation#^35aeb2|therefore also continuous]]. Therefore, let $h(t)=f'(t)$ be a continuous and $m-2$ differentiable function. This process can be continued $f$ is not defined to be continuous anymore and follows the proof of the [[5 - Fourier Convergence#^e8a98c|main theorem]], where in the [[5.1 - Proof Preliminaries#^e3e352|Riemann-Lebesgue lemma]] the function $g(x)$ has additionally the factor $k^{r-1}$ with $1 \leq r \leq m$ . $$\tag*{$\square$}$$

## Differentiability and Convergence

>[!theorem] Continuity and Uniform Convergence for Exponential Series ([[../../../PDFs/howell2016.pdf#page=210|Source]])
>Let $f$ be a periodic function with period $p$ and
>$$\mathcal{F}[f]|_{t}=\sum_{k=-\infty}^\infty k^m c_{k}e^{i2\pi \omega_{k}t}$$
>Assume, further, that $f$ is piecewise smooth and continuous, and for convenience, let
>$$B= \frac{1}{2\pi}\left( p \int _{\text{ period}}\lvert f'(t) \rvert^2  \, dt  \right)^{1/2}$$
>Then
>1. The series $\sum_{k=-\infty}^\infty$ converges absolutely with
>$$\begin{align}
> \sum_{k=-\infty}^{-N-1}\lvert c_{k} \rvert \leq \frac{B}{\sqrt{ N }} \tag{1}\\
> \sum_{k=N+1}^{\infty}\lvert c_{k} \rvert \leq \frac{B}{\sqrt{ N }}
>\end{align}$$
>for $N=1,2,3,\dots$
>2. The Fourier series for $f$ converges uniformly to $f$. Moreover, for any real value $t$ and any pair of positive integers $M$ and $N$,
>$$\left\lvert f(t)- \sum_{k=-M}^N k^m c_{k}e^{i2\pi \omega_{k}t}\right\rvert \leq \left[\frac{1}{\sqrt{ M }}+\frac{1}{\sqrt{ N }}\right]B $$