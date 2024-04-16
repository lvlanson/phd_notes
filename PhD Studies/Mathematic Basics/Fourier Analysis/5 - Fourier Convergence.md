>[!recall] Recall Convergence Types
>>[!recall] Pointwise Convergence
>>Pointwise convergence occurs when a sequence of functions converges to a limit function at each point in the domain. In other words, for each value of $x$ in the domain, the sequence of function values converges to the corresponding value of the limit function. Pointwise convergence does not require that the convergence be uniform across the entire domain.
>
>>[!recall] Uniform Convergence
>>Uniform convergence, on the other hand, occurs when a sequence of functions converges to a limit function uniformly across the entire domain. In other words, the rate of convergence is the same at every point in the domain, and the difference between the sequence of function values and the limit function becomes arbitrarily small as n approaches infinity.
>
>>[!recall] Absolute Convergence
>> Absolute convergence occurs when a series of functions converges absolutely, meaning that the sum of the absolute values of the function values converges to a finite limit. Absolute convergence implies pointwise convergence, but not necessarily uniform convergence.

## Pointwise Convergence

>[!theorem] Theorem Basic Theorem on Pointwise Convergence ([[../../../PDFs/howell2016.pdf#page=165|Source]])
>Let $f$ be a periodic, piecewise continuous function with
>$$\mathcal{F}[f]|_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i_{2}\pi \omega_{k}t}$$
>period $p$ and $\omega_{k}= \frac{k}{p}$. Further assume, that $f$ is piecewise smooth on an interval $(a,b)$, and let $t_{0}$ be any point in that interval. Then
>1. If $f(t)$ is continuous at $t=t_{0}$, then $\mathcal{F}[f]|_{t_{0}}$ converges pointwise, i.e. $$\sum_{k=-\infty}^\infty c_{k}e^{i 2 \pi \omega_{k}t_{0}}=f(t_{0})$$
>2. If $f(t)$ has a jump discontinuity at $t=t_{0}$, then $$\lim_{ N \to \infty } \sum_{k=-N}^N c_{k}e^{i 2 \pi \omega_{k}t_{0}} = \frac{1}{2}\Bigg[\lim_{ \tau \to t_{0}^-}f(\tau) + \lim_{ \tau \to \tau_{0}^+ }f(\tau)  \Bigg]$$

>[!theorem] Theorem Pointwise Convergence for Trigonometric Series ([[../../../PDFs/howell2016.pdf#page=166|Source]])
>Let $f$ be a periodic, piecewise continuous function with period $p$ and $\omega_{k}= \frac{k}{p}$. Further assume, that $f$ is piecewise smooth on an interval $(a,b)$, and let $t_{0}$ be any point in that interval. Then the trigonometric Fourier series for $f$ (see [[1 - Classical Fourier Series#^046566|definition trigonometric Fourier series]])
>$$A_{0} + \sum_{k=1}a_{k} \cos(2\pi \omega_{k}t) + b_{k}\sin(2\pi \omega_{k}t)$$
>1. If $f(t)$ is continuous at $t=t_{0}$, then  $$A_{0} + \sum_{k=1}a_{k} \cos(2\pi \omega_{k}t_{0}) + b_{k}\sin(2\pi \omega_{k}t_{0}) = f(t_{0})$$
>2. If $f(t)$ has a jump discontinuity at $t=t_{0}$, then $$A_{0} + \sum_{k=1}a_{k} \cos(2\pi \omega_{k}t_{0}) + b_{k}\sin(2\pi \omega_{k}t_{0}) = \frac{1}{2}\Bigg[\lim_{ \tau \to t_{0}^-}f(\tau) + \lim_{ \tau \to \tau_{0}^+ }f(\tau)  \Bigg]$$

>[!theorem] Fourier's Theorem (Part 1) ([[../../../PDFs/howell2016.pdf#page=166|Source]])
>Let $f$ be a periodic, piecewise smooth function on $\mathbb{R}$ and let $\mathcal{F}[f]$ be either the trigonometric or complex exponential Fourier series for $f$. Then $\mathcal{F}[f]$ converges at every point where $f$ is continuous, and
>$$f = \mathcal{F}[f]$$
>as piecewise continuous functions.

>[!theorem] Fourier's Theorem (Part 2) ([[../../../PDFs/howell2016.pdf#page=169|Source]])
>Let $f$ be a piecewise continuous, periodic function on $\mathbb{R}$, and let $\mathcal{F}[f]$ be either the trigonometric or complex exponential Fourier series for $f$. Assume further that, on each finite interval, $f$ is smooth at all but a finite number (possibly zero) of points. Then, on each finite interval, $\mathcal{F}[f]|_{t}$ converges to $f(t)$ at all but a finite number of points, and so, $f= \mathcal{F}[f]$ as piecewise continuous functions on $\mathbb{R}$.

## Uniform and Nonuniform Approximations

>[!lemma] Lemma Jump Discontinuity Error ([[../../../PDFs/howell2016.pdf#page=172|Source]])
>Let $f$ and $S$ be two functions on the real line with $f$ being piecewise continuous and $S$ being continuous. Assume $f$ has a nontrivial discontinuity with a jump $j_{0}$ at some point $t_{0}$. Then there is a nontrivial interval $(a,b)$ such that
>1. $f$ is continuous over $(a,b)$ and
>2. $\lvert f(t)-S(t) \rvert> \frac{1}{4}\lvert j_{0} \rvert$ for every $t$ in $(a,b)$

>[!theorem] Theorem Discontinuity Errors Implications ([[../../../PDFs/howell2016.pdf#page=172|Source]])
>Let $f$ be a periodic, piecewise continuous function. If the Fourier series $\mathcal{F}[f]$ over $\sum_{k=M}^N$, denoted as $\mathcal{F}_{M,N}[f]|_{t}$, with $M < N$ is uniformly approximate $f$, then $f$ must be a continuous function on the entire real line
>
>Conversely, if $f$ is not a continuous function on the entire real line, then the Fourier series $\mathcal{F}_{M,N}[f]|_{t}$ do not uniformly approximate $f$. 
>
>Moreover, if $f$ has a jump of $j_{0}$ at $t_{0}$, then, for each pair of integers $M$ and $N$ with $M < N$, there is an interval containing $t_{0}$ or with $t_{0}$ as an endpoint over which
>$$\lvert f(t) - \mathcal{F}_{M,N}[f]|_{t} \rvert > \frac{1}{4} \lvert j_{0} \rvert  $$

>[!theorem] Theorem Continuity and Uniform Convergence for Exponential Series ([[../../../PDFs/howell2016.pdf#page=173|Source]])
>
>Let $f$ be a piecewise smooth and periodic function with period $p$. If $f$ is also continuous, then its Fourier series
>$$\sum_{k=-\infty}^\infty c_{k} e^{i 2 \pi \omega_{k}t}$$
>converges uniformly to $f$. Moreover, for any real value $t$ and any pair of integers $M$ and $N$ with $M < 0 < N$
>$$\left\lvert  f(t) - \sum_{k=M}^N c_{k}e^{i 2 \pi \omega_{k} t} \right\rvert  \leq \left[ \frac{1}{\sqrt{ \lvert M \rvert  }} +\frac{1}{\sqrt{ \lvert N \rvert  }} \right]B$$
>where
>$$B= \frac{1}{2 \pi} \left( p \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt  \right)^{1/2}$$

>[!remark]
>This theorem requires a function to be **continuous and piecewise smooth** to have uniform convergence properties for the respective Fourier series.

>[!theorem] Theorem Error Approximation for Trigonometric Fourier Series ([[../../../PDFs/howell2016.pdf#page=173|Source]])
>Let $f$ be a periodic, piecewise continuous function with trigonometric Fourier series
>$$A_{0} + \sum_{k=1}^\infty a_{k} \cos(2\pi \omega_{k}t) + b_{k} \sin(2 \pi \omega_{k}t)$$
>If there is a finite integer $N_{\varepsilon}$ for each $\varepsilon> 0$ such that
>$$\left\lvert  f(t) - A_{0} -\sum_{k=1}^N a_{k} \cos(2\pi \omega_{k}t) + b_{k} \sin(2 \pi \omega_{k}t)\right\rvert \leq \varepsilon$$
>for every real value $t$ and every integer $N \geq N_{\varepsilon}$, then $f$ is continous on the entire real line. Conversely, if $f$ has a nonzero jump of $j_{0}$ at $t_{0}$, then, for any positive integer $N$, there is an interval containing $t_{0}$ or with $t_{0}$ as an endpoint over which
>$$\left\lvert f(t) - A_{0} -\sum_{k=1}^N a_{k} \cos(2\pi \omega_{k}t) + b_{k} \sin(2 \pi \omega_{k}t)\right\rvert > \frac{1}{4}\lvert j_{0} \rvert  $$

>[!theorem] Theorem Continuity and Uniform Convergence for Trigonometric Series ([[../../../PDFs/howell2016.pdf#page=173|Source]])
> Let $f$ be a continuous and piecewise smooth periodic function with period $p$. Then its trigonometric Fourier series 
>$$A_{0} + \sum_{k=1}^\infty a_{k} \cos(2\pi \omega_{k}t) + b_{k} \sin(2 \pi \omega_{k}t)$$
>converges uniformly to $f$. Moreover, for any real value of $t$ and any positive integer $N$
>$$\left\lvert f(t) - A_{0} -\sum_{k=1}^N a_{k} \cos(2\pi \omega_{k}t) + b_{k} \sin(2 \pi \omega_{k}t)\right\rvert \leq \frac{B}{\sqrt{ N }}$$
>where
>$$B= \frac{1}{\pi}\left( p \int _{\text{period}} \lvert f'(t) \rvert ^2 \, dt  \right)^{1/2}$$