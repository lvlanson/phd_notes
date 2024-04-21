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

## Approximations for Discontinuous Functions

>[!remark] Remark Gibbs Phenomenon
> The Gibbs phenomenon describes the "strong wiggling" around the discontinuieties. Let 
> $$f(t)= \begin{cases}
> 0 & \text{ if } - \pi < t <0 \\
> 1 & \text{ if } 0 < t < \pi \\
> f(t-2\pi) &\text{ in general}
>\end{cases}$$
>![[figures/Gibbs_Phenomenon.png  | center]]
>with (a) being the $N=10$ partial sum and (b) being the $N=25$ partial sum.
>>[!observation] 
>>As $N$ increases the interval of significance decreases.

>[!theorem] Theorem Gibbs Deviation Factor ([[../../../PDFs/howell2016.pdf#page=176|Source]])
>Let $f$ be a periodic, piecewise smooth function with period $p$ and
>$$\mathcal{F}[f]|_{t} = \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}$$
>If $f$ has a jump of $j_{0}$ at $t_{0}$, then
>$$\lim_{ N \to \infty } \left[ \sum_{k=-N}^N c_{k}e^{i 2 \pi \omega_{k}(t_{0}+t_{{N,m}})}-f(t_{0}+t_{N,m}) \right] = \begin{cases}
> - \gamma_{m} j_{0} & \text{ if } m <0 \\
> \gamma_{m} j_{0} & \text{ if } 0 < m
>\end{cases}$$
>where
>$$\begin{align}
> t_{N,m} &= \begin{cases}
> \frac{mp}{2N} &\text{ if } m \text{ is even} \\
> \frac{mp}{2N+2} & \text{ if } m \text{ is odd}
>\end{cases} \\[1em]
> \gamma_{m} &= \frac{1}{2}- \frac{1}{\pi}\int _{0}^{m\pi} \frac{\sin(\tau)}{\tau} \, d\tau  \\
> j_{0} &= \frac{1}{2}\left[ \lim_{ t \to t_{0}^+ }f(t) + \lim_{ t \to t_{0}^- } f(t) \right]   \\[1em]
> M_{N} &= \begin{cases}
> N-1 & \text{ if } N \text{ is even} \\
> N & \text{ if } N \text{ is odd}
>\end{cases}
>\end{align}$$
>with $m \in[-M_{N}, M_{N}]\subset \mathbb{Z}$
>>[!note] Note on Parameter Description
>>- $N$ - describes the amount of terms used for the partial Fourier sum. It is possible to imagine $N$ to be the equidistant discretization of $f$ on the given period, where on a period we have $2N$ discrete points. 
>>- $m$ - is a parameter to shift the attention to an oscillation local extremum with $t_{N,m}$. Note, that the partial Fourier series determines with $N$ what the highest frequency used for approximation is, hence we have $N$ periods for the highest frequency and on a single period we have $2$ extrema, hence $2N$ extrema in sum
>>- $t_{N,m}$ - describes the specific extrema of the Fourier oscillations with respect to the highest frequency, i.e. $-M_{N}\leq m \leq M_{N}$
>>- $M_{N}$ - determines the amount of local extrema described by the Fourier series. Note, if $N$ is even, there will be exactly $2N-1$ different extrema, because there will be an identical extremum over the period $[a,b]$ exactly at $a$ and $b$. 
>>- $j_{0}$ - describes the magnitude of the jump of the discontinuity
>>- $y_{m}$ - describes the deviation factor with respect to the magnitude of the jump $j_0$ at $m$
>
>>[!note] Note on the Interpretation of the Theorem
>>The term 
>>$$\sum_{k=-N}^N c_{k}e^{i 2 \pi \omega_{k}(t_{0}+t_{{N,m}})}-f(t_{0}+t_{N,m})$$
>>describes the deviation of the Fourier approximation and the actual function values of the discontinuous function. Since we add the limit operator with $N \to \infty$ we extend the bounded set of points $M_N$ to an unbounded interval $m \in [-\infty, \infty] = \mathbb{Z}$. 
>>
>>If we consider a finite amount of $m$, then there will be a highest frequency with a corresponding discrete set of extrema. Since $N \to \infty$ the oscillation granularity will become a continuous set of extrema, since there are infinitely many extrema created by the infinitely high frequencies. Therefore, we get a continuous deviation evaluation caused by the discontinuity.
>
>>[!proof]
>> Assume $f$ has a single discontinuity in the interval $0 \leq t < p$ at $t_{0}$.

>[!theorem] Theorem Approximation Error for Discontinuous Functions ([[../../../PDFs/howell2016.pdf#page=177|Source]])
>Suppose $f$ is a periodic, piecewise smooth function with period $p$ and $t$ is any fixed real value. Let $K$ be the number of points in the half-closed interval $\left[ t-\frac{p}{2}, t+\frac{p}{2} \right)$ at which $f$ is discontinuous, and let $t_{1},t_{2}, \dots, t_{K}$ be those points of discontinuity with $j_{k}$ denoting the jump in $f$ at $t_{k}$. Then, for any pair of integers $M$ and $N$ with $M < 0 < N$
>$$E_{MN}(t)\leq \left[ \frac{1}{\sqrt{ \lvert M \rvert  }} + \frac{1}{\sqrt{ \lvert N \rvert  }}\right]B_{0} + \left[ \frac{1}{1-2m} + \frac{1}{1+2N} \right] \sum_{k=1}^K B_{K}(t)$$
>where 
>$$B_{0}= \frac{1}{2\pi}\left( p \int _{\text{period}}\left\lvert  f'(t)+\frac{1}{p}\sum^K_{k=1}j_{k}  \right\rvert^2  \, dt  \right)^{1/2}$$
>and for $k=1,2,\dots,K$
>$$B_{k}(t)= \lvert j_{k} \rvert \left[ \frac{1}{\pi}-\frac{1}{\pi^2}+\frac{1}{\pi \sin\left( \frac{\pi}{p} \lvert t-t_{k} \rvert  \right)} \right] $$

## Convergence in Norm

^a2c7f7

>[!def] Definition Convergence in Norm ([[../../../PDFs/howell2016.pdf#page=178|Source]])
>Let $f$ be a periodic, piecewise continuous function with period $p$ and Fourier series
>$$\mathcal{F}[f]|_{t} = \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}$$
>we say a Fourier series **converges in norm** (or in energy) to $f$ if and only if 
>$$\lim_{ \substack{N \to \infty \\ M \to \infty} } \left\lvert \left\lvert  f(t)-\sum_{k=M}^N c_{k}e^{i 2 \pi \omega_{k}t}  \right\rvert \right\rvert=0$$
>>[!note]
>>This statement is equivalent to that the error converges in norm to 0 as $M\to-\infty$ and $N\to \infty$, i.e.
>>$$\lim_{ \substack{N \to \infty \\ M \to \infty} } \left\lvert \left\lvert E_{MN}(t)  \right\rvert \right\rvert=0$$

>[!lemma] Lemma Convergence in Norm of Fourier Series ([[../../../PDFs/howell2016.pdf#page=179|Source]])
>The (complex exponential) Fourier series for a continuous, piecewise smooth, periodic function converges in norm to that function.

>[!lemma] Lemma Convergence in Norm of Fourier Series ([[../../../PDFs/howell2016.pdf#page=180|Source]])
>Let $f$ be a periodic, piecewise continuous function with
>$$\mathcal{F}[f]|_{t} = \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}$$
>Then the Fourier series for $f$ converges in norm to $f$ if and only if
>$$p \sum_{k=-\infty}^\infty \lvert c_{k} \rvert^2 = \lvert\lvert f \rvert\rvert^2 \tag{Bessel's Equality}$$

^6fe4cc

>[!lemma] Lemma Parseval's Equality ([[../../../PDFs/howell2016.pdf#page=180|Source]])
>Let $f$ and $g$ be two piecewise continuous, periodic functions with the same period $p$ and with Fourier series
>$$\begin{align}
> \mathcal{F}[f]|_{t} = \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t} \\
> \mathcal{F}[g]|_{t} = \sum_{k=-\infty}^\infty \tilde{c}_{k}e^{i 2\pi \omega_{k}t} \\
>\end{align}$$
>Assume, in addition, that $g$ is continuous and piecewise smooth, then
>1. $\sum\limits_{k=-\infty}^\infty c_{k}\tilde{c}^*_{k}$ converges absolutely
>2. $\left\langle f\,,\,g \right\rangle= p\sum_{k=-\infty}^\infty c_{k}\tilde{c}^*_{k}$ (Parseval's Equality for Fourier Series)
>
>>[!proof]-
>>1. We use [[3 - Inner Products, Norms and Orthogonality#^5b7f44| Bessel's inequality]] 
>>$$\begin{align}
>> \sum_{k=1}^N \lvert c_{k} \rvert^2 \lvert\lvert \phi_{k} \rvert\rvert^2 \leq \lvert\lvert f \rvert\rvert^2   
>>\end{align}$$
>>Note, we are using the [[4 - Complex Exponential Fourier Series| complex exponential Fourier series]]. As we [[4 - Complex Exponential Fourier Series#^aaa10f|derived]] it, we extended the range of the $k$ into the negatives and use the complex exponential form
>>$$\sum_{k=-N}^N \lvert c_{k} \rvert^2 \lvert\lvert e^{-i 2 \pi \omega_{k}t} \rvert\rvert^2 \leq \lvert\lvert f \rvert\rvert^2   $$
>>We can compute the [[3 - Inner Products, Norms and Orthogonality#^7c5e1e| norm]] of the exponential using [[3 - Inner Products, Norms and Orthogonality#^e3ca10|inner product]]. For simplicity assume that the period is defined over the interval $[0,p]$
>>$$\begin{align}
>> \lvert\lvert e^{-i 2 \pi \omega_{k}t} \rvert\rvert^2 &= \left\langle e^{-i 2 \pi \omega_{k}t}\,,\,e^{-i 2 \pi \omega_{k}t} \right\rangle  \\
>> &= \int_{0}^p e^{-i 2 \pi \omega_{k}t}(e^{-i 2 \pi \omega_{k}t})^* \, dt  \\
>> &= \int_{0}^p e^{-i 2 \pi \omega_{k}t}e^{+i 2 \pi \omega_{k}t} \, dt  \\
>> &= \int_{0}^p e^{0} \, dt  \\ 
>> &= p
>>\end{align}$$
>>Therefore, we get 
>>$$\begin{align}
>> \sum_{k=-N}^N \lvert c_{k} \rvert^2 \lvert\lvert e^{-i 2 \pi \omega_{k}t} \rvert\rvert^2 \leq \lvert\lvert f \rvert\rvert^2  &\iff p\sum_{k=-N}^N \lvert c_{k} \rvert^2  \leq \lvert\lvert f \rvert\rvert^2  \\
>> &\iff \sum_{k=-N}^N \lvert c_{k} \rvert^2  \leq \frac{1}{p}\lvert\lvert f \rvert\rvert^2 
>>\end{align}$$
>>We can now make the following assertion for both of the functions
>>$$\begin{align}
>> \sum_{k=-\infty}^\infty \lvert c_{k} \rvert^2 &\leq \frac{1}{p} \lvert\lvert f \rvert\rvert^2 \tag{1a}\\  
>> \sum_{k=-\infty}^\infty \lvert \tilde{c}_{k} \rvert^2 &\leq \frac{1}{p} \lvert\lvert g \rvert\rvert^2   \tag{1b}
>>\end{align}$$
>>We now show the first claim using the previous results and the [[../Functional Analysis/Functional Analysis Basics#^8d565e|Cauchy-Schwarz inequality]]
>>$$\begin{align}
>> \sum_{k=-\infty}^\infty \lvert c_{k}\tilde{c}_{k}^* \rvert &= \sum_{k=-\infty}^\infty \lvert c_{k} \rvert \, \lvert \tilde{c}_{k} \rvert  \tag{Complex Property} \\
>> &\leq \left( \sum_{k=-\infty}^\infty \lvert c_{k} \rvert^2 \right)^{1/2}  \left( \sum_{k=-\infty}^\infty \lvert \tilde{c}_{k} \rvert^2 \right)^{1/2} \tag{Cauchy-Schwarz} \\
>> &\leq \lvert\lvert f \rvert\rvert \; \lvert\lvert g \rvert\rvert \tag{Result 1b, 1a Root}   \\
>>\end{align}$$
>>$$\tag*{$\square$}$$
>>
>>2. Let $M < 0 < N$ and 
>>$$E_{MN}(t) = g(t)- \sum_{k=M}^N \tilde{c}_{k}e^{i 2 \pi \omega_{k}t}$$
>>Since $g$ is continuous and piecewise smooth we know by the [[#^a2c7f7| vanishing error in norm]] that
>>$$\lim_{ \substack{N \to \infty \\ M \to - \infty} } E_{MN}(t) = 0$$
>>Using the [[3 - Inner Products, Norms and Orthogonality#^e3ca10| inner product]] and [[3 - Inner Products, Norms and Orthogonality#^e14b2d| Cauchy-Schwarz inequality]] we get
>>$$\begin{align}
>>\lim_{ \substack{N \to \infty \\ M \to - \infty} } \lvert \left\langle f\,,\,E_{MN} \right\rangle  \rvert &= \lim_{ \substack{N \to \infty \\ M \to - \infty} } \lvert\lvert f \rvert\rvert \; \underbrace{ \lvert\lvert E_{MN} \rvert\rvert }_{ =0 } = 0 \tag{3}
>>\end{align}$$
>>Computing the [[3 - Inner Products, Norms and Orthogonality#^e3ca10| inner product]] without the limit operator, we have using [[#^6fe4cc| convergence properties]]
>>$$\begin{align}
>> \left\langle f\,,\,E_{MN} \right\rangle &= \int _{\text{period}} f(t)\left( g(t)- \sum^N_{k=M} \tilde{c}_{k}e^{i 2 \pi \omega_{k}t} \right)^*\, dt  \\
>>  &= \int _{\text{period}} f(t)\left( g(t)^*- \sum^N_{k=M} \tilde{c}_{k}e^{-i 2 \pi \omega_{k}t} \right)\, dt  \\
>>  &= \int _{\text{period}} f(t) g(t)^*- \sum^N_{k=M} \tilde{c}_{k}f(t)e^{-i 2 \pi \omega_{k}t} \, dt  \\
>>  &= \int _{\text{period}} f(t) g(t)^*\, dt -\int _{\text{period}} \sum^N_{k=M} \tilde{c}_{k}f(t)e^{-i 2 \pi \omega_{k}t} \, dt  \\
>>  &= \underbrace{ \int _{\text{period}} f(t) g(t)^*\, dt }_{ =\left\langle f\,,\,g \right\rangle  } -\sum^N_{k=M} \tilde{c}_{k}\underbrace{ \int _{\text{period}} f(t)e^{-i 2 \pi \omega_{k}t} \, dt }_{ =\lvert\lvert f \rvert\rvert^2  }  \\
>>  &= \left\langle f\,,\,g \right\rangle  -\sum^N_{k=M} \tilde{c}_{k}pc_{k} \tag{Convergence Property}\\
>>\end{align}$$
>>Rearranging gives
>>$$\begin{align}
>> \left\langle f\,,\,g \right\rangle = \left\langle f\,,\,E_{MN} \right\rangle +  p\sum^N_{k=M} c_{k}\tilde{c}_{k}
>>\end{align}$$
>>Now using the limit operator and result $(3)$ we get
>>$$\begin{align}
>>\left\langle f\,,\,g \right\rangle &= \lim_{ \substack{N \to \infty \\ M \to - \infty} } \left( \left\langle f\,,\,E_{MN} \right\rangle +  p\sum^N_{k=M} c_{k}\tilde{c}_{k} \right) \\
>> &= 0 + p \sum^\infty_{k=-\infty} c_{k}\tilde{c}_{k} \\
>> &= p \sum^\infty_{k=-\infty} c_{k}\tilde{c}_{k} \tag*{$\square$}
>>\end{align}$$
>
>>[!remark]
>> This lemma doesn't require $g$ to be continuous but rather piecewise continuous. It was given since the tools to prove it are not given yet under the general conditions.

>[!Theorem] Theorem Parseval's Equality ([[../../../PDFs/howell2016.pdf#page=180|Source]])
>Let $f$ and $g$ be two piecewise continuous, periodic functions with the same period $p$ and with Fourier series
>$$\begin{align}
> \mathcal{F}[f]|_{t} = \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t} \\
> \mathcal{F}[g]|_{t} = \sum_{k=-\infty}^\infty \tilde{c}_{k}e^{i 2\pi \omega_{k}t} \\
>\end{align}$$
>1. $\sum\limits_{k=-\infty}^\infty c_{k}\tilde{c}^*_{k}$ converges absolutely
>2. $\left\langle f\,,\,g \right\rangle= p\sum_{k=-\infty}^\infty c_{k}\tilde{c}^*_{k}$ (Parseval's Equality for Fourier Series)


>[!lemma] Corollary Bessel's Equality ([[../../../PDFs/howell2016.pdf#page=182|Source]])
>Let $f$ be a piecewise continuous, periodic function with Fourier series
>$$\mathcal{F}[f]|_{t} = \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t} $$
>then
>$$\lvert\lvert f \rvert\rvert^2 = p \sum_{k=-\infty}^\infty \lvert c_{k} \rvert^2 $$


>[!theorem] Theorem Norm Convergence ([[../../../PDFs/howell2016.pdf#page=182|Source]])
>The (complex exponential) Fourier series for a piecewise continuous, periodic function converges in norm to that function


>[!remark]
>The next part for theorems about the sine and cosine Fourier series are omitted. They can be found [[../../../PDFs/howell2016.pdf#page=182|here]].