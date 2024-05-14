## Fundamentals

>[!def] Definition Trigonometric Fourier Series ([[../../../PDFs/howell2016.pdf#page=113|Source]])
>Let $f$ be a periodic function with period $p$ where $p$ is some positive number. The (trigonometric) Fourier series $\mathcal{FS}$ for $f$ is the infinite series
>$$\mathcal{FS}[f]\rvert_{t} = A_{0} + \sum_{k=1}^\infty \Big[ a_{k} \cos\big(2\pi \omega_{k}t\big) + b_{k} \sin\big(2\pi \omega_{k}t\big)\Big]$$
>where, for $k = 1,2,3, \dots$
>$$\begin{align}
> \omega_{k} &= \frac{k}{p} \tag{Frequency Coefficient}\\
> A_{0} &= \frac{1}{p} \int _{0}^p f(t) \, dt \tag{Trigonometric Coefficient}\\
> a_{k} &= \frac{2}{p} \int _{0}^p f(t) \cos(2\pi \omega_{k}t) \, dt \tag{Trigonometric Coefficient}\\
> b_{k} &= \frac{2}{p} \int _{0}^p f(t) \sin(2\pi \omega_{k}t) \, dt \tag{Trigonometric Coefficient}\\
>\end{align}$$

^046566

>[!lemma] 
>If $f$ is either a constant function, a sine function or a cosine function, then
>$$\mathcal{FS}[f]|_{t} = f(t)$$
>Especially,
>$$\mathcal{FS}[0]|_{t} = 0$$
>>[!proof]- Proof Constant Function $f(t) = c$
>>$$\begin{align}
>> A_{0} &= \frac{1}{p}\int_{0}^p f(t) \, dt\\  
>> &= \frac{1}{p}\int_{0}^p c \, dt\\  
>> &= \frac{1}{p}\left[ct\right]_{0}^p  \\  
>> &= \cancel{ \frac{p}{p} }c  \\ 
>> &= c   \\ \\ \\
>> a_{k} &= \frac{2}{p}\int _{0}^p f(t)\cos(2\pi \omega_{k} t) \, dt  \\
>> &= \frac{2}{p} \int _{0}^p c \cos(2\pi \omega_{k}t) \, dt \\
>> &= \frac{2c}{p} \Big[2\pi \omega_{k}\sin(2\pi \omega_{k}t)\Big]_{0}^p \\
>> &= \frac{2c}{p} \Big(2\pi \omega_{k}\big(\sin(2\pi \omega_{k}t) - \underbrace{ \sin(0) }_{ =0 }\big)\Big) \\
>> &= \frac{2c}{p} \left( 2\pi \omega_{k}\underbrace{ \sin\left( 2\pi \frac{k}{\cancel{ p }}\cancel{ p }  \right) }_{ =0 } \right) \tag*{$\left( \omega_{k}=\frac{k}{p} \right)$}\\
>> &= 0 \\ \\ \\
>> b_{k} &= \frac{2}{p} \int _{0}^p f(t)\sin(2\pi \omega_{k}t)\, dt \\
>>  &= \frac{2}{p}  \int _{0}^p c\sin(2\pi \omega_{k}t)\, dt \\
>>  &= \frac{2c}{p}   \Big[ -2\pi \omega_{k}\cos( 2\pi \underbrace{ \omega_{k} }_{ =\dfrac{k}{p} }t )\Big]_{0}^p \\
>>  &= \frac{2c}{p}   \Big( -2\pi \omega_{k}\big(\underbrace{ \cos( 2\pi k) }_{ =1 }-\underbrace{ \cos( 0) }_{ =1 }\big)\Big) \\
>>  &= \frac{2c}{p}   \Big( -2\pi \omega_{k}\cdot 0 \Big) \\
>>  &= 0 \\ \\ \\
>>\mathcal{FS}[f]|_{t}  &= \underbrace{ A_{0} }_{ =c } + \sum_{k=1}^\infty \Big[ \underbrace{ a_{k} }_{ =0 } \cos\big(2\pi \omega_{k}t\big) + \underbrace{ b_{k} }_{ =0 } \sin\big(2\pi \omega_{k}t\big)\Big] \\
>> &= c
>>\end{align}$$
>
>>[!proof]- Proof Sine Function $f(t)=\sin(2\pi \gamma t)$
>>Note $\gamma$ is some fixed value. Therefore, the period can be given as
>>$$p = \frac{1}{\gamma} \quad \Rightarrow \quad \gamma = \frac{1}{p}$$
>>We now compute the Fourier series
>>$$\begin{align}
>> A_{0} &= \frac{1}{p}\int _{0}^p  f(t)\, dt \\ 
>>    &= \frac{1}{p}\int _{0}^p  \sin\left(  \frac{2\pi }{p} t\right)\, dt \\ 
>>    &= \frac{1}{p}\left[-\cos\left( \frac{2\pi}{p}t \right)\right]_{0}^p\\
>>    &= \frac{1}{p}\left(\underbrace{ -\cos\left( 2\pi \right) }_{ =-1 }  \underbrace{+ \cos(0) }_{ =1 }\right) \\
>>    &= 0
>>\end{align}$$
>>Note, $\sin$ is an odd function and integrates to $0$ over its period. Now we make use of the [[../Trigonometry/Trigonometric Identities#^282081|trigonometric product identities]] to solve $a_0$. Note, since the product of and odd and even function yields another odd function, it must evaluate to $0$ anyways. But we will make the effort to show it properly.
>>$$\begin{align}
>> a_{0} &= \frac{2}{p}\int _{0}^p f(t)\cos(2\pi \omega_{k}t) \, dt \\ 
>>  &= \frac{2}{p}\int _{0}^p \sin\left( \frac{2\pi}{p}t \right)\cos(2\pi \omega_{k}t) \, dt  \\
>>  &= \frac{2}{p}\int _{0}^p \frac{1}{2}\left(\sin\left( \frac{2\pi}{p}t + 2\pi \omega_{k}t \right) + \sin\left( \frac{2\pi}{p}t - 2\pi \omega_{k}t \right)\right) \, dt  \\
>>  &= \frac{1}{p}\int _{0}^p \left(\sin\left( \frac{2\pi}{p}t (1+k) \right) + \sin\left( \frac{2\pi}{p}t (1 - k) \right)\right) \, dt \tag*{$\left( \omega _{k}=\frac{k}{p} \right)$} \\
>>  &= \frac{1}{p} \left[ -\frac{p}{2\pi(1+k)}\cos\left( \frac{2\pi}{p}t (1+k) \right) - \frac{p}{2\pi(1-k)}\cos\left( \frac{2\pi}{p}t (1 - k) \right) \right]_{0}^p\\
>>  &= \frac{1}{p} \Bigg( -\frac{p}{2\pi(1+k)}\underbrace{ \cos\left( \frac{2\pi}{\cancel{ p }}\cancel{ p } (1+k) \right) }_{ =1 } - \frac{p}{2\pi(1-k)}\underbrace{ \cos\left( \frac{2\pi}{\cancel{ p }}\cancel{ p } (1 - k)  \right) }_{ =1 } \\
>>  &\quad\;-\Bigg(- \frac{p}{2\pi(1+k)}\underbrace{ \cos(0) }_{ =1 }-\frac{p}{2\pi(1-k)}\underbrace{ \cos(0) }_{ =1 } \Bigg)\Bigg)\\
>>  &= \frac{1}{p} \left(- \frac{p}{2\pi(1+k)} + \frac{p}{2\pi(1+k)} -  \frac{p}{2\pi(1-k)} + \frac{p}{2\pi(1-k)}\right)\\
>>  &= 0
>>\end{align}$$
>> We continue now with $b_k$. First, we require $k\neq 1$. We will highlight the line, where this requirement will be important to hold as equation $(*)$
>> $$\begin{align}
>> b_{k} &= \frac{2}{p} \int _{0}^p f(t) \sin(2\pi \omega_{k}t)\, dt \\
>> &= \frac{2}{p} \int _{0}^p \sin\left( \frac{2\pi}{p}t \right) \sin(2\pi \omega_{k}t)\, dt \\
>> &= \frac{2}{p} \int _{0}^p \frac{1}{2}\left( \cos\left( \frac{2\pi}{p}t - 2\pi \omega_{k} t \right) - \cos\left( \frac{2\pi}{p}t + 2\pi \omega_{k}t \right) \right) \, dt  \\
>> &= \frac{1}{p} \int _{0}^p \cos\left( \frac{2\pi}{p}t (1-k) \right)- \cos\left( \frac{2\pi}{p}t (1+k) \right) \, dt  \\
>> &= \frac{1}{p} \left[\frac{p}{2\pi(1-k)}\sin\left( \frac{2\pi}{p}t (1-k) \right)-\frac{p}{2\pi(1+k)} \sin\left( \frac{2\pi}{p}t (1+k) \right) \right]_{0}^p \\
>> &= \frac{1}{p} \Bigg(\frac{p}{2\pi(1-k)}\underbrace{ \sin\left( \frac{2\pi}{\cancel{ p }}\cancel{ p } (1-k) \right) }_{ =0 }-\frac{p}{2\pi(1+k)} \underbrace{ \sin\left( \frac{2\pi}{\cancel{ p }}\cancel{ p } (1+k) \right) }_{ =0 }  \\
>> &\quad\;-\Bigg(\frac{p}{2\pi(1-k)}\underbrace{ \sin\left(0 \right) }_{ =0 }-\frac{p}{2\pi(1+k)} \underbrace{ \sin\left(0 \right) }_{ =0 }\Bigg) \Bigg)  \tag{*} \\
>> &= 0
>>\end{align}$$
>>The highlighted line does not allow $k=1$ as $1-k$ in the denominator would yield an undefined expression, i.e. dividing by zero. Now we set $k=1$
>>$$\begin{align}
>> b_{k} &= \frac{2}{p} \int _{0}^p f(t) \sin(2\pi \omega_{k}t)\, dt \\
>> &= \frac{2}{p} \int _{0}^p \sin^2\left( \frac{2\pi}{p}t \right) \, dt \\
>> &= \frac{2}{p} \int _{0}^p \frac{1}{2} \left(1-\cos\left( \frac{4\pi}{p}t \right)\right) \, dt \\
>> &= \frac{1}{p} \left[t - \frac{p}{4\pi} \sin\left( \frac{4\pi}{p}t \right)\right]_{0}^p \\
>> &= \frac{1}{p} \left(p - \frac{p}{4\pi} \underbrace{ \sin\left( \frac{4\pi}{\cancel{ p }}\cancel{ p } \right) }_{ =0 }\right) \\ 
>> &= 1
>>\end{align}$$
>>Therefore, $b_k$ evaluates to
>>$$b_{k} = \begin{cases}
>> 0 &\text{if } k\neq 1  \\
>> 1 &\text{if } k = 1
>>\end{cases}$$
>>Inserting the found values yields
>>$$\begin{align}
>>FS[f]|_{t}  &= \underbrace{ A_{0} }_{ =0 } + \sum_{k=1}^\infty \Big[ \underbrace{ a_{k} }_{ =0 } \cos\big(2\pi \omega_{k}t\big) + \underbrace{ b_{k} }_{ =\begin{cases}
0 &\text{if } k\neq1 \\
1 & \text{if } k = 1
\end{cases} } \sin\big(2\pi \omega_{k}t\big)\Big] \\
>> &= 1 \cdot \sin(2\pi \omega_{1}t) \\
>> &= \sin\left( 2\pi \frac{1}{p} t \right)  \\
>> &= \sin(2\pi \gamma t) \tag*{$\square$}
>>\end{align}$$

>[!remark]
> Fourier series can be defined over any integration limits, as long as they are of length $p$, which is the length of the period of $f$.


>[!property] Property Alternative Intervals for Integration ([[../../../PDFs/howell2016.pdf#page=120|Source]])
> Let $f$ be a periodic function of period length $p$, then the integration limits can be given arbitrary as long as they cover the period interval
> $$\begin{align}
> A_{0} &= \frac{1}{p} \int _{\text{period}} f(t) \, dt \\
> a_{k} &= \frac{2}{p} \int _{\text{period}} f(t) \cos(2\pi \omega_{k}t) \, dt \\
> b_{k} &= \frac{2}{p} \int _{\text{period}} f(t) \sin(2\pi \omega_{k}t) \, dt \\
> \end{align}$$

## Symmetry Properties

>[!def] Definition Even and Odd Functions ([[../../../PDFs/olson2017.pdf#page=37|Source]])
>A function $f$ is said to be **even** if
>$$ f(t) = f(-t)$$
>A function $f$ is said to be **odd** if
>$$ f(t) = -f(-t)$$
>>[!example]-
>> - $\cos(kt)$ is even
>> - $\sin(kt)$ is odd
>> - $t^k$ with $k \text{ mod } 2 = 0$ is even (monomial)
>> - $t^k$ with $k \text{ mod } 2 = 1$ is odd (monomial)
>>
>>>[!note]
>>> If $f$ is odd we have
>>> $$\int _{-T}^T f(t) \, dt = 0 $$
>>> If $f$ is even we have
>>> $$\int _{-T}^T f(t) \, dt = 2\int _{0}^T f(t) \, dt $$


>[!property]
>The product of two functions being
>- even and even -> even
>- even and odd -> odd
>- odd and odd -> even

>[!theorem] Theorem Fourier Series for Odd Functions ([[../../../PDFs/howell2016.pdf#page=122|Source]])
>Let $f$ be a periodic, piecewise continuous function with period $p$. If $f$ is an **odd** function on $\mathbb{R}$, then its trigonometric Fourier series is given by
>$$\mathcal{FS}[f]|_{f}= \sum_{k=1}^\infty b_{k} \sin(2\pi \omega_{k}t)$$
>where for $k=1,2,3,\dots$
>$$\begin{align}
> \omega_{k} &= \frac{k}{p} \\
> b_{k} &= \frac{4}{p} \int _{0}^{p/2} f(t) \sin\left( \frac{2\pi k}{p}t \right)\, dt 
>\end{align}$$
>>[!proof]-
>>Let $f$ be an odd, piecewise continuous function with period length $p$, then the Fourier series can be given as 
>>$$\begin{align}
>> \omega_{k} &= \frac{k}{p}\\
>> A_{0} &= \frac{1}{p} \int _{0}^p f(t) \, dt \\
>> a_{k} &= \frac{2}{p} \int _{0}^p f(t) \cos(2\pi \omega_{k}t) \, dt \\
>> b_{k} &= \frac{2}{p} \int _{0}^p f(t) \sin(2\pi \omega_{k}t) \, dt \\
>>\end{align}$$
>>according to the [[#^046566| definition of trigonometric Fourier series]]. We will now show that according to the properties of **odd functions**, the above given terms are in fact the result of the properties.
>>1. $A_0$
>>$$\begin{align}
>> A_{0} &= \frac{1}{p}\int _{0}^p f(t) \, dt \\
>> &= \frac{1}{p}\int _{-p/2}^{p/2} f(t) \, dt \\ 
>> &= 0 \tag{Odd Function}
>>\end{align}$$
>>2. $a_{k}$
>>$$\begin{align}
>> a_{k} &= \frac{2}{p}\int _{0}^p f(t)\cos(2\pi \omega_{k}t) \, dt  \\
>> &= \frac{2}{p}\int _{-p/2}^{p/2} f(t)\cos(2\pi \omega_{k}t) \, dt \tag{Odd times Odd}\\
>> &= 0 \tag{Odd Function}
>>\end{align}$$
>>3. $b_{k}$
>>$$\begin{align}
>> b_{k} &= \frac{2}{p}\int _{0}^p f(t)\sin(2\pi \omega_{k}t)\, dt  \\
>> &=\frac{2}{p}\int _{-p/2}^{p/2} f(t)\sin(2\pi \omega_{k}t) \, dt \tag{Even times Odd} \\
>> &= 2 \cdot \frac{2}{p}\int _{0}^{p/2} f(t)\sin(2\pi \omega_{k}t) \, dt \tag{Even Function} \\
>> &=  \frac{4}{p}\int _{0}^{p/2} f(t)\sin(2\pi \omega_{k}t) \, dt 
>>\end{align}$$
>>$$\tag*{$\square$}$$

^3277d9

>[!Theorem] Fourier Series for Even Functions ([[../../../PDFs/howell2016.pdf#page=122|Source]])
>Let $f$ be a periodic, piecewise continuous function with period $p$. If $f$ is an **even** function on $\mathbb{R}$, then its trigonometric Fourier series is given by
>$$\mathcal{FS}[f]|_{t} = A_{0} + \sum_{i=1}^\infty a_{k} \cos(2\pi \omega_{k}t)$$
>where 
>$$A_{0} = \frac{2}{p}\int_{0}^{p/2} f(t)\, dt $$
>where for $k=1,2,3,\dots$
>$$\begin{align}
> \omega_{k} &= \frac{k}{p} \\
> a_k &= \frac{4}{p}\int _{0}^{p/2}f(t) \, dt 
>\end{align}$$
>>[!proof]-
>>Let $f$ be even, piecewise continuous with period length $p$ , then the Fourier series can be given as
>>$$\begin{align}
>> \omega_{k} &= \frac{k}{p}\\
>> A_{0} &= \frac{1}{p} \int _{0}^p f(t) \, dt \\
>> a_{k} &= \frac{2}{p} \int _{0}^p f(t) \cos(2\pi \omega_{k}t) \, dt \\
>> b_{k} &= \frac{2}{p} \int _{0}^p f(t) \sin(2\pi \omega_{k}t) \, dt \\
>>\end{align}$$
>>according to the [[#^046566| definition of trigonometric Fourier series]]. We will now show that according to the properties of **even functions**, the above given terms are in fact the result of the properties.
>>1. $A_{0}$
>>$$\begin{align}
>> A_{0} &= \frac{1}{p}\int _{0}^p f(t)\, dt  \\
>>    &= \frac{1}{p}\int _{-p/2}^{p/2} f(t)\, dt   \\
>>    &= \frac{2}{p}\int _{0}^p f(t)\, dt \tag{Even Function}
>>\end{align}$$
>>2. $a_{k}$
>>$$\begin{align}
>> a_{k} &= \frac{2}{p} \int _{0}^p f(t)\cos(2\pi \omega_{k}t)\, dt \\ 
>>  &= \frac{2}{p} \int _{-2/p}^{2/p} f(t)\cos(2\pi \omega_{k}t)\, dt \tag{Even times Even}\\ 
>>  &= \frac{4}{p} \int _{0}^{2/p} f(t)\cos(2\pi \omega_{k}t)\, dt \tag{Even Function}\\ 
>>\end{align}$$
>>3. $b_{k}$
>>$$\begin{align}
>> b_{k} &= \frac{2}{p}\int _{0}^p f(t)\sin(2\pi \omega_{k}t)\, dt \tag{Even times Odd} \\
>>    &= 0 \tag{Odd Function} 
>>\end{align}$$
>>$$\tag*{$\square$}$$

^7e4728

## Linearity

>[!lemma] Lemma Linearity of Fourier Transformation ([[../../../PDFs/howell2016.pdf#page=123|Source]])
>Let $f,g$ and $h$ be periodic piecewise continuous functions, all with period $p$. Assume that, for some pair of constants $\gamma$ and $\lambda$ we have
>$$f = \lambda g + \gamma h$$
>then
>$$A_{0} = \gamma A_{0}^g + \lambda A_{0}^h$$
>and for $k=1,2,3,\dots$
>$$\begin{align}
> a_{k}^f &= \gamma a_{k}^g + \lambda a_{k}^h \\
> b_{k}^f &= \gamma b_{k}^g + \lambda b_{k}^h
>\end{align}$$
>>[!proof] Proof omitted

>[!theorem] Theorem Linearity of Fourier Transformation ([[../../../PDFs/howell2016.pdf#page=123|Source]])
>Let $N$ be a finite positive integer; let $f_{1},f_{2},\dots,f_{N}$ all be periodic, piecewise continuous functions with common period, and let $\alpha_{1},\alpha_{2}, \alpha_{3}, \dots, \alpha_{N}$ all be constants, then
>$$\begin{align}
> \mathcal{FS}\left[\sum^N_{n=1}\alpha_{n}f_{n}\right]\Bigg|_{t} = \sum_{n=1}^N \alpha_{n}\mathcal{FS}[f_{n}]|_{t}
>\end{align}$$
>>[!proof] Proof Omitted

>[!Corollary] Corollary ([[../../../PDFs/howell2016.pdf#page=125|Source]])
>If $f$ can be expressed as a finite linear combination of a **constant function with sine and cosine functions** (with common period), then that linear combination is the trigonometric Fourier series for $f$, i.e.
>$$\mathcal{FS}[f]|_{t} = f(t)$$

## Scaling and Shifting

>[!theorem] Theorem Scaling of Fourier Series ([[../../../PDFs/howell2016.pdf#page=125|Source]])
> Let $f$ be a periodic, piecewise continuous function with period $p$ and Fourier series
> $$\mathcal{FS}[f]|_{t} = A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) + b_{k}\sin(2\pi \omega_{k}t)\Big]$$
> If $g(t) = f(\alpha t)$ for some $\alpha > 0$, then $g$ is a periodic, piecewise continuous function with period $\widehat{p} = \frac{p}{\alpha}$. Moreover, letting $\widehat{\omega }_{k}= \frac{k}{\widehat{p}}= \alpha \omega_{k}$,
> $$\mathcal{FS}[g]|_{t}= A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \widehat{\omega }_{k}t) + b_{k}\sin(2\pi \widehat{\omega }_{k}t)\Big]$$
>>[!proof]-
>>Note $f$ is a periodic function with period $p$, then by definition of periodic functions we have
>>$$f(x-p) = f(p)$$
>>Now we stretch the periodicity by $\alpha$ and we get 
>>$$\begin{align}
>> g(x) &= f(\alpha x) \\
>>&=f(\alpha(x-\widehat{p}))  \\
>>&= f(\alpha x - \alpha \widehat{p})
>>\end{align}$$
>>We have the following relation
>>$$\begin{align}
>> p &= \alpha \widehat{p} \\
>> \widehat{p} &= \frac{p}{\alpha} \tag*{$\square$}
>>\end{align}$$

>[!theorem] Theorem Negative Input of Fourier Series ([[../../../PDFs/howell2016.pdf#page=125|Source]])
>Let $f$ be a periodic, piecewise continuous function with period $p$ and Fourier series
>$$\mathcal{FS}[f]|_{f} = A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) + b_{k}\sin(2\pi \omega_{k}t)\Big]$$
>If $g(t)=f(-t)$, then $g$ is a periodic, piecewise continuous function with period $p$ and trigonometric Fourier series
>$$\mathcal{FS}[g]|_{t} = A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) - b_{k}\sin(2\pi \omega_{k}t)\Big]$$
>>[!proof]

>[!theorem] Theorem Half Period Shift ([[../../../PDFs/howell2016.pdf#page=125|Source]])
>Let $f$ be a periodic, piecewise continuous function with period $p$ and Fourier series
>$$\mathcal{FS}[f]|_{f} = A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) + b_{k}\sin(2\pi \omega_{k}t)\Big]$$
>If $g(t) = f\left( t- \frac{p}{2} \right)$, then $g$ is periodic, piecewise continuous function with period $p$ and 
>$$\mathcal{FS}[g]|_{t} = A_{0} + \sum_{k=1}^\infty \Big[(-1)^k a_{k} \cos(2\pi \omega_{k}t) + (-1)^k b_{k}\sin(2\pi \omega_{k}t)\Big]$$
>>[!proof]

## Partial Sums

>[!def] Definition Partial Sum Approximation ([[../../../PDFs/howell2016.pdf#page=127|Source]])
>Let $f$ be a periodic, piecewise continuous function with trigonometric Fourier series
> $$\mathcal{FS}[f]\rvert_{t} = A_{0} + \sum_{k=1}^\infty \Big[ a_{k} \cos\big(2\pi \omega_{k}t\big) + b_{k} \sin\big(2\pi \omega_{k}t\big)\Big]$$
>The partial sum approximation is given as a Fourier series with $N$ as its upper limit
>$$\mathcal{FS}_{N}[f]\rvert_{t} = A_{0} + \sum_{k=1}^N \Big[ a_{k} \cos\big(2\pi \omega_{k}t\big) + b_{k} \sin\big(2\pi \omega_{k}t\big)\Big]$$