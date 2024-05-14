## Differentiation of Fourier Series

>[!lemma] Lemma Fourier Series of a Derivative ([[../../../PDFs/howell2016.pdf#page=207|Source]])
>Assume $f$ is a periodic, continuous, [[../Calculus/Differentiation#^680da2|piecewise smooth]] function with period $p$ and 
>$$\mathcal{FS}[f]|_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i2\pi \omega_{k}t}$$
>then
>$$\begin{align}
> \mathcal{FS}[f']|_t &= \sum_{k=-\infty}^\infty i2\pi \omega_{k}c_{k}e^{i2\pi \omega_{k}t} \\
> &= \frac{i 2\pi}{p}\sum_{k=-\infty}^\infty kc_{k}e^{i2\pi \omega_{k}t}
>\end{align}$$
>>[!proof]-
>>Let 
>>$$\begin{align}
>> \mathcal{FS}[f]|_{t} &= \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}\\
>> \mathcal{FS}[f']|_{t} &= \sum_{k=-\infty}^\infty d_{k}e^{i 2\pi \omega_{k}t}\\
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
>>$$\mathcal{FS}[f']|_{t} = \sum_{k=-\infty}^\infty \underbrace{ i2\pi \omega_{k}c_{k} }_{ =d_{k} }e^{i 2\pi \omega_{k}t} \tag*{$\square$}$$
>

>[!theorem] Theorem Differentiation of Fourier Series ([[../../../PDFs/howell2016.pdf#page=207|Source]])
>Let $f$ be a periodic, continuous, [[../Calculus/Differentiation#^680da2|piecewise smooth]] function with period $p$ and
>$$\mathcal{FS}[f]|_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i2\pi \omega_{k}t}$$
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
> $$\mathcal{FS}[f]|_{t}= A_{0}+ \sum_{k=1}^\infty a_{k}\cos(2 \pi \omega_{k}t) + b_{k}\sin(2 \pi \omega_{k}t)$$
> Then
> $$\begin{align}
> \mathcal{FS}[f']|_{t} &= \sum_{k=1}^\infty -2\pi \omega_{k}a_{k}\cos(2 \pi \omega_{k}t) + 2\pi \omega_{k}b_{k}\sin(2 \pi \omega_{k}t)\\
> &= \frac{2\pi}{p}\sum_{k=1}^\infty - ka_{k}\cos(2 \pi \omega_{k}t) + kb_{k}\sin(2 \pi \omega_{k}t)
>\end{align}$$
>>[!proof] Proof Omitted -> Follows from the Exponential Fourier Series

>[!theorem] Theorem Differentiation of Trigonometric Fourier Series ([[../../../PDFs/howell2016.pdf#page=209|Source]])
>Let $f$ be a periodic, continuous, [[../Calculus/Differentiation#^680da2|piecewise smooth]] function with period $p$ and 
> $$\mathcal{FS}[f]|_{t}= A_{0}+ \sum_{k=1}^\infty a_{k}\cos(2 \pi \omega_{k}t) + b_{k}\sin(2 \pi \omega_{k}t)$$
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
> f^{(m)}&= \sum_{k=-\infty}^\infty \frac{d^m}{dt^m}\Big[c_{k}e^{i 2\pi \omega_{k}t}\Big] \\
> &= \left( \frac{i2\pi}{p} \right)^m \sum_{k=-\infty}^\infty k^m c_{k}e^{i 2 \pi \omega_{k}t}
>\end{align}$$
>>[!proof]-
>>Note, the case for $m=1$ is the [[#^bbe431|theorem of differentiating Fourier series]] and is therefore already shown. Assume $m>1$, then $f'(t)$ is differentiable and [[../Calculus/Differentiation#^35aeb2|therefore also continuous]]. Therefore, let $h(t)=f'(t)$ be a continuous and $m-2$ differentiable function. This process can be continued $f$ is not defined to be continuous anymore and follows the proof of the [[5 - Fourier Convergence#^e8a98c|main theorem]], where in the [[5.1 - Proof Preliminaries#^e3e352|Riemann-Lebesgue lemma]] the function $g(x)$ has additionally the factor $k^{r-1}$ with $1 \leq r \leq m$ . $$\tag*{$\square$}$$

^ef6e98

## Differentiability and Convergence

>[!theorem] Theorem - Estimation Bounds: Continuity and Uniform Convergence for Exponential Series ([[../../../PDFs/howell2016.pdf#page=210|Source]])
>Let $f$ be a periodic function with period $p$ and
>$$\mathcal{FS}[f]|_{t}=\sum_{k=-\infty}^\infty k^m c_{k}e^{i2\pi \omega_{k}t}$$
>Assume, further, that $f$ is piecewise smooth and continuous, and for convenience, let
>$$B= \frac{1}{2\pi}\left( p \int _{\text{ period}}\lvert f'(t) \rvert^2  \, dt  \right)^{1/2}$$
>Then
>1. The series $\sum_{k=-\infty}^\infty c_{k}$ converges absolutely with
>$$\begin{align}
> \sum_{k=-\infty}^{-N-1}\lvert c_{k} \rvert \leq \frac{B}{\sqrt{ N }} \tag{1}\\
> \sum_{k=N+1}^{\infty}\lvert c_{k} \rvert \leq \frac{B}{\sqrt{ N }}
>\end{align}$$
>for $N=1,2,3,\dots$
>2. The Fourier series for $f$ converges uniformly to $f$. Moreover, for any real value $t$ and any pair of positive integers $M$ and $N$,
>$$\left\lvert f(t)- \sum_{k=-M}^N k^m c_{k}e^{i2\pi \omega_{k}t}\right\rvert \leq \left[\frac{1}{\sqrt{ M }}+\frac{1}{\sqrt{ N }}\right]B $$
>
>>[!proof]-
>>###### Preparation
>>---
>>Let 
>>$$\begin{align}
>> \mathcal{FS}[f]|_{t} &= \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}\\
>> \mathcal{FS}[f']|_{t} &= \sum_{k=-\infty}^\infty d_{k}e^{i 2\pi \omega_{k}t}\\
>>\end{align}$$
>>with
>>$$\begin{align}
>> c_{k} &= \frac{1}{p}\int _{0}^p f(t)e^{-i 2\pi \omega_{k}t} \, dt  \\
>> d_{k} &= \frac{i2\pi k}{p}c_{k} \tag{1}
>>\end{align}$$
>>We observe
>>$$d_{0}=\frac{i 2\pi0}{p}c_{0}=0$$ 
>>and using equation $(1)$ and taking the norm on both sides
>>$$\begin{alignat}{2}
>> \lvert c_{k} \rvert &= \frac{p}{\lvert k \rvert 2\pi } \lvert d_{k} \rvert \tag{2}
>>\end{alignat}$$
>>We make the following observation for $\lvert d_{k} \rvert$ using the [[../Calculus/Integration#^a5bf98|absolute value integral]].
>>$$\begin{align}
>> \lvert d_{k} \rvert &= \left\lvert  \frac{1}{p}\int _{\text{period}}f'(t)e^{-i 2\pi \omega t} \, dt   \right\rvert  \\
>>  &\leq   \frac{1}{p}\int _{\text{period}}\left\lvert f'(t)e^{-i 2\pi \omega t}\right\rvert \, dt     \tag{Absolute Value Int.} \\
>> &= \frac{1}{p}\int _{\text{period}} \lvert f'(t) \rvert \;\underbrace{ \lvert e^{-i 2 \pi \omega_{k}t} \rvert }_{ =1 }   \, dt \\
>> &= \frac{1}{p} \int _{\text{period}} \lvert f'(t) \rvert  \, dt \tag{3}
>>\end{align}$$
>>Plugging the result into equation $(2)$ gives the relation
>>$$\begin{align}
>> \lvert c_{k} \rvert &\leq \frac{\cancel{ p }}{\lvert k \rvert 2\pi } \frac{1}{\cancel{ p }} \int _{\text{period}} \lvert f'(t) \rvert  \, dt \\
>> \lvert c_{k} \rvert &\leq \frac{1}{\lvert k \rvert 2\pi }  \int _{\text{period}} \lvert f'(t) \rvert  \, dt \tag{4}
>>\end{align}$$
>>>[!note]- Note $\lvert e^{-i 2 \pi \omega_{k}t}  \rvert$  (Pythagorean Identity)
>>> $$\begin{align}
>>> \lvert e^{-i 2 \pi \omega_{k}t}  \rvert &= \lvert \cos(-2\pi \omega_{k}t)+ i\sin(-2\pi \omega_{k}t) \rvert \\
>>> &= \sqrt{ \cos^2(-2\pi \omega_{k}t)+\sin^2(-2\pi \omega_{k}t) }  \\
>>> &= \sqrt{ 1 } \\
>>> &= 1
>>>\end{align}$$
>>---
>>1. We will show only one of the bounds, the other one follows by adjusting accordingly
>>First we use the result of equation $(2)$ and the [[3 - Inner Products, Norms and Orthogonality#^e14b2d|Cauchy-Schwarz inequality]], therefore let $N \in \mathbb{Z}^+$
>>$$\begin{align}
>> \sum_{k=N+1}^\infty \lvert c_{k} \rvert &=  \sum_{k=N+1}^\infty \frac{p}{2\pi \lvert k \rvert }\lvert d_{k} \rvert  \\
>> &= \frac{p}{2\pi}\sum_{k=N+1}^\infty \frac{1}{\lvert k \rvert }\lvert d_{k} \rvert \\
>> &= \frac{p}{2\pi}\left( \sum_{k=N+1}^\infty \frac{1}{k^2} \right)^{1/2}\left( \sum_{k=N+1}^\infty \lvert d_{k} \rvert^2 \right)^{1/2}  \tag{Cauchy-Schwarz (5)}
>>\end{align}$$
>>Note, equality holds in the last line, since $\lvert c_{k} \rvert = \frac{p}{\lvert k \rvert 2\pi } \lvert d_{k} \rvert$ implies that $\lvert d_{k} \rvert$ and $\frac{1}{k}$ are proportional (i.e. linearly dependent, see [[../Functional Analysis/Lectures/B1 - Hilbert Spaces#^3fd445|Cauchy-Schwarz Inequality]]). <br>
>>We further validate that $\sum_{k=N+1}^\infty \frac{1}{k^2}$ converges by using [[../Calculus/Series#^c7f7dd|the integral test]]. We see
>>$$\sum_{k=N+1}^\infty \frac{1}{k^2} \leq \int _{N}^\infty \frac{1}{x^2} \, dx = \frac{1}{N} \tag{6}$$
>>Further we also estimate the second term using [[3 - Inner Products, Norms and Orthogonality#^5b7f44| Bessel's inequality]] and the assertions of equation $(3)$
>>$$\begin{align}
>> \sum_{k=N+1}^\infty \lvert d_{k} \rvert^2 &\leq \sum_{k=-\infty}^\infty \lvert d_{k} \rvert^2 \\
>>  &\leq \underbrace{ \frac{1}{p} \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt }_{ =\lvert\lvert f \rvert\rvert  } \tag{7}\\
>>\end{align}$$
>> We use these inequalities on equation $(5)$, so we continue
>> $$\begin{align}
>>  \sum_{k=N+1}^\infty \lvert c_{k} \rvert &= \frac{p}{2\pi}\left( \sum_{k=N+1}^\infty \frac{1}{k^2} \right)^{1/2}\left( \sum_{k=N+1}^\infty \lvert d_{k} \rvert^2 \right)^{1/2} \\
>> &\leq \frac{p}{2\pi}\left( \frac{1}{N} \right)^{1/2}\left( \frac{1}{p} \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt  \right)^{1/2} \\
>> &=\frac{1}{2\pi}\left( \frac{1}{N} \right)^{1/2}(p^2)^{1/2}\left( \frac{1}{p} \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt  \right)^{1/2} \\
>> &=\left( \frac{1}{N} \right)^{1/2}\underbrace{ \frac{1}{2\pi}\left( p \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt  \right)^{1/2} }_{ =B }  \\
>> &= \frac{B}{\sqrt{ N }} 
>>\end{align}$$
>>Hence, we have
>>$$\begin{align}
>>\sum_{k=N+1}^\infty \lvert c_{k} \rvert \leq \frac{B}{\sqrt{ N }} \tag*{$\square$}
>>\end{align}$$
>>---
>>2. We start by using the fact that an infinite Fourier series can perfectly represent a continuous and piecewise smooth function $f$.
>>$$\begin{align}
>> \left\lvert  f(t)- \sum_{k=-M}^N c_{k}e^{i 2\pi \omega_{k}t}  \right\rvert &= \left\lvert  \sum_{k=-\infty}^\infty c_{k}e^{i 2 \pi \omega_{k}t} - \sum_{k=-M}^N c_{k}e^{i 2\pi \omega_{k}t} \right\rvert  \\
>> &= \left\lvert  \sum_{k=-\infty}^{-M+1} c_{k}e^{i 2 \pi \omega_{k}t} + \sum_{k=N+1}^\infty c_{k}e^{i 2\pi \omega_{k}t} \right\rvert  \\
>> &\leq  \sum_{k=-\infty}^{-M+1} \big|c_{k}e^{i 2 \pi \omega_{k}t}\big| + \sum_{k=N+1}^\infty \big|c_{k}e^{i 2\pi \omega_{k}t}\big| \tag{TI} \\
>> &= \underbrace{ \sum_{k=-\infty}^{-M+1} \big|c_{k}\big| }_{ \leq\frac{B}{\sqrt{ M }}  } + \underbrace{ \sum_{k=N+1}^\infty \big|c_{k}\big| }_{ \leq\frac{B}{\sqrt{ N }} } \tag{$\lvert e^{i 2\pi \omega_{k}t} \rvert = 1 $} \\
>> &\leq \frac{B}{\sqrt{ M }} + \frac{B}{\sqrt{ N }} \\
>> &= \left[ \frac{1}{\sqrt{ M }} + \frac{1}{\sqrt{ N }} \right]B \tag*{$\square$}
>>\end{align}$$

^79a237

>[!theorem] Theorem Estimation Bounds: Smoothness and Uniform Convergence for Exponential Series ([[../../../PDFs/howell2016.pdf#page=212|Source]])
>Let $f$ be a periodic function with period $p$ and
>$$\mathcal{FS}[f]|_{t}=\sum_{k=-\infty}^\infty k^m c_{k}e^{i2\pi \omega_{k}t}$$
>Let $m$ be a positive integer, and assume $f$ is $m$-times differentiable and $f^{(m)}$ is piecewise continuous. Let
>$$B=\left( \frac{p}{2\pi} \right)^m \left( \frac{1}{p(2m-1)} \int _{\text{period}} \Big\lvert f^{(m)}(t) \Big\rvert^2 \, dt  \right)$$
>Then
>1. The series $\sum_{k=-\infty}^\infty c_{k}$ converges absolutely for $N \in \mathbb{Z}$ with
>$$\begin{align}
> \sum_{k=-\infty}^{-N-1}\lvert c_{k} \rvert &\leq \frac{B}{\sqrt{ N^{2m-1} }}  \\
> \sum_{k=N+1}^{\infty}\lvert c_{k} \rvert &\leq \frac{B}{\sqrt{ N^{2m-1} }}  \\
>\end{align}$$
>2. The Fourier series for $f$ converges uniformly to $f$. Moreover, for any real value $t$ and any pair of positive integers $M$ and $N$
>$$\left\lvert  f(t)- \sum_{k=-M}^N c_{k}e^{i2\pi \omega_{k}t}  \right\rvert \leq \left[ \frac{1}{\sqrt{ M^{2m-1} }}+\frac{1}{\sqrt{ N^{2m-1} }} \right]B $$
>
>>[!proof]-
>>###### Preparation
>>---
>>We use the results of the previous proof. First note, that by [[#^ef6e98| higher order differentiations of exponential series]] we have the relation
>>$$f^{(m)}= \left( \frac{i 2\pi}{p} \right)^m \sum_{k=-\infty}^\infty k^mc_{k}e^{i2\pi \omega_{k}t}$$
>>For the Fourier series of the $m$-th derivative we have
>>$$\mathcal{FS}[f^{(m)}]|_{t}=\sum_{k=-\infty}^\infty d_{k}e^{i 2\pi \omega_{k}t}$$
>>with 
>>$$d_{k}=\left( \frac{i 2\pi k}{p} \right)^m c_{k}$$
>>We are interested in confirming absolute convergence, therefore, we analyze the norm of the given expression, hence
>>$$\begin{align}
>> \lvert d_{k} \rvert &=\left\lvert  \frac{i2\pi k}{p}  \right\rvert^m \lvert c_{k} \rvert   \\
>> &= \lvert k \rvert^m \left( \frac{2\pi}{p} \right)^m \lvert c_{k} \rvert  
>>\end{align} $$
>>We rearrange for $\lvert c_{k} \rvert$ to prepare the estimation of the relation to $\lvert d_{k} \rvert$, i.e.
>>$$\lvert c_{k} \rvert = \lvert d_{k}  \rvert \left( \frac{p}{2\pi \lvert k \rvert } \right)^m \tag{1}$$
>> We again estimate $\lvert d_{k} \rvert$ by using the identity on the series of the derivative
>> $$\begin{align}
>> \lvert d_{k} \rvert &=  \left\lvert \frac{1}{p} \int _{0}^p f^{(m)}(t)e^{-i 2\pi \omega_{k}t} \, dt   \right\rvert  \\
>> &\leq \frac{1}{p}\int _{0}^p \lvert f^{(m)}(t)\underbrace{ e^{-i 2\pi \omega_{k}t} }_{ \lvert e^{-i 2\pi \omega_{k}t} \rvert =1  } \rvert  \, dt \tag{Absolute Value Int.} \\
>> &= \frac{1}{p}\int _{0}^p \lvert f^{(m)}(t) \rvert  \, dt \tag{Pythagorean Identity}
>>\end{align}$$
>>Further we continue to estimate using [[3 - Inner Products, Norms and Orthogonality#^5b7f44| Bessel's inequality]]
>>$$\begin{align}
>> \sum_{k=N+1}^\infty \lvert d_{k} \rvert^2 &\leq \sum_{k=-\infty}^\infty \lvert d_{k} \rvert^2 \\
>>  &\leq \underbrace{ \frac{1}{p} \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt }_{ =\lvert\lvert f \rvert\rvert  } \tag{2}\\
>>\end{align}$$
>>We use this relation on the found identity in equation $(1)$ and give an estimate using $\lvert d_{k} \rvert$
>> $$\begin{align}
>> \lvert c_{k} \rvert &\leq   \left( \frac{p}{2\pi \lvert k \rvert } \right)^m \frac{1}{p}\int _{0}^p \lvert f^{(m)}(t) \rvert  \, dt \\
>> &= p^{m-1}(2\pi \lvert k \rvert )^{-m} \int _{0}^p \lvert f^{(m)}(t) \rvert \, dt
>>\end{align}$$
>>---
>>1. Having prepared these results, we can prove the first claim. We use the relation found in equation $(1)$ to make the following assertion using the [[3 - Inner Products, Norms and Orthogonality#^e14b2d|Cauchy-Schwarz inequality]] using the linear dependence of the $\lvert c_{k} \rvert$ and $\lvert d_{k} \rvert$
>>$$\begin{align}
>> \sum_{k=N+1}^{\infty} \lvert c_{k} \rvert &= \sum_{k=N+1}^{\infty} \lvert d_{k}  \rvert \left( \frac{p}{2\pi \lvert k \rvert } \right)^m \\ 
>> &= \left( \frac{p}{2\pi} \right)^m\sum_{k=N+1}^{\infty} \lvert d_{k}  \rvert  \frac{1}{ \lvert k \rvert^m }  \\
>> &= \left( \frac{p}{2\pi} \right)^m \left( \sum_{k=N+1}^\infty  \frac{1}{  k^{2m} }\right)^{1/2}\left( \sum_{k=N+1}^\infty \lvert d_{k}  \rvert^2\right)^{1/2} \tag{Cauchy-Schwarz}
>>\end{align}$$
>>We estimate the convergence limit of $\sum_{k=N+1}^\infty  \frac{1}{  k^{2m}}$ using the [[../Calculus/Series#^c7f7dd|integral test]]
>>$$\begin{align}
>> \sum_{k=N+1}^\infty  \frac{1}{  k^{2m} } &\leq \int_{N}^\infty \frac{1}{x^{2m}} \, dx \\
>> &= \left[ \frac{1}{-2m+1}x^{-2m+1} \right]_{N}^\infty \\
>> &= \lim_{ t \to \infty } \left[ \frac{1}{-2m+1}x^{-2m+1} \right]_{N}^t \\
>> &=  \lim_{ t \to \infty } \Bigg( \underbrace{ \frac{1}{-2m+1}\underbrace{ t^{-2m+1} }_{ \to0 } }_{ =0 } - \frac{1}{-2m+1}N^{-2m+1} \Bigg)_{N}^t \\
>> &= \frac{1}{2m-1}N^{-2m+1}
>>\end{align}$$
>>Now, we use this estimate to continue estimating  $\sum_{k=N+1}^{\infty} \lvert c_{k} \rvert$. We continue at 
>>$$\begin{align}
>> \sum_{k=N+1}^{\infty} \lvert c_{k} \rvert &= \left( \frac{p}{2\pi} \right)^m \left( \sum_{k=N+1}^\infty  \frac{1}{  k^{2m} }\right)^{1/2}\left( \sum_{k=N+1}^\infty \lvert d_{k}  \rvert^2\right)^{1/2} \\
>> &\leq \left( \frac{p}{2\pi} \right)^m  \left(\frac{1}{2m-1}N^{-2m+1}\right)^{1/2} \left(\frac{1}{p} \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt\right)^{1/2}  \\ \\
>> &=\frac{1}{\sqrt{ N^{2m+1} }} \underbrace{ \left( \frac{p}{2\pi} \right)^m \left(\frac{1}{p(2m-1)} \int _{\text{period}} \lvert f'(t) \rvert^2  \, dt\right)^{1/2} }_{ =B } \\
>> &=\frac{B}{\sqrt{ N^{2m-1} }}
>>\end{align}$$
>>Therefore, we establish the relation
>>$$\sum_{k=N+1}^{\infty} \lvert c_{k} \rvert \leq \frac{B}{\sqrt{ N^{2m-1} }} \tag*{$\square$}$$
>>---
>>
>>2. The second part is a straight forward computation using the property that $f(t)$ can be estimated by a Fourier series because it is piecewise continuous and $m$-times differentiable, hence piecewise smooth
>>$$\begin{align}
>> \left\lvert  f(t)- \sum_{k=-M}^N c_{k}e^{i 2\pi \omega_{k}t}  \right\rvert &= \left\lvert  \sum_{k=-\infty}^\infty c_{k}e^{i 2 \pi \omega_{k}t} - \sum_{k=-M}^N c_{k}e^{i 2\pi \omega_{k}t} \right\rvert  \\
>> &= \left\lvert  \sum_{k=-\infty}^{-M+1} c_{k}e^{i 2 \pi \omega_{k}t} + \sum_{k=N+1}^\infty c_{k}e^{i 2\pi \omega_{k}t} \right\rvert  \\
>> &\leq  \sum_{k=-\infty}^{-M+1} \big|c_{k}e^{i 2 \pi \omega_{k}t}\big| + \sum_{k=N+1}^\infty \big|c_{k}e^{i 2\pi \omega_{k}t}\big| \tag{TI} \\
>> &= \underbrace{ \sum_{k=-\infty}^{-M+1} \big|c_{k}\big| }_{ \leq\frac{B}{\sqrt{ M^{2m-1} }}  } + \underbrace{ \sum_{k=N+1}^\infty \big|c_{k}\big| }_{ \leq\frac{B}{\sqrt{ N^{2m-1} }}} \tag{$\lvert e^{i 2\pi \omega_{k}t} \rvert = 1 $} \\
>> &= \left[\frac{1}{\sqrt{ M^{2m-1} }} + \frac{1}{\sqrt{ N^{2m-1} }}\right]B
>>\end{align}$$
>> This establishes the relation
>> $$\begin{align}
>> \left\lvert  f(t)- \sum_{k=-M}^N c_{k}e^{i 2\pi \omega_{k}t}  \right\rvert \leq \left[\frac{1}{\sqrt{ M^{2m-1} }} + \frac{1}{\sqrt{ N^{2m-1} }}\right]B \tag*{$\square$}
>>\end{align}$$

>[!theorem] Theorem Uniform Convergence for Trigonometric Series ([[../../../PDFs/howell2016.pdf#page=213|Source]])
>Let $f$ be a periodic function with period $p$ and
>$$\mathcal{FS}[f]|_{t}= A_{0} + \sum_{k=1}^\infty a_{k} \cos(2 \pi \omega_{k}t) + b_{k}\sin(2 \pi \omega_{k}t)$$
>Let $m$ be a positive integer, and assume $f$ is $m$-times differentiable and $f^{(m)}$ is piecewise continuous. Let
>$$B=\left( \frac{p}{2\pi} \right)^m \left( \frac{1}{p(2m-1)} \int _{\text{period}} \Big\lvert f^{(m)}(t) \Big\rvert^2 \, dt  \right)$$
>Then:
>1. The series $\sum_{k=1}^\infty a_{k}$ and $\sum_{k=1}^\infty b_{k}$ both converge absolutely for $N \in \mathbb{Z}$ with
> $$\begin{align}
> \sum_{k=N+1}^\infty \lvert a_{k} \rvert &\leq \frac{2B}{\sqrt{ N^{2m-1} }}  \\
> \sum_{k=N+1}^\infty \lvert b_{k} \rvert &\leq \frac{2B}{\sqrt{ N^{2m-1} }}  \\
>\end{align}$$
>2. The Fourier series for $f$ converges uniformly to $f$. Moreover, for any real value $t$ and any positive integer $N$,
>$$\left\lvert  f(t)- A_{0} - \sum_{k=1}^\infty a_{k} \cos(2 \pi \omega_{k}t) + b_{k}\sin(2 \pi \omega_{k}t)  \right\rvert \leq \left[ \frac{1}{\sqrt{ M^{2m-1} }}+\frac{1}{\sqrt{ N^{2m-1} }} \right]B $$
>
>>[!proof] Proof omitted
>>

>[!theorem] Reverse Theorem: Uniqueness and Necessity of Fourier Coefficients ([[../../../PDFs/howell2016.pdf#page=213|Source]])
>Assume $\sum_{k=-\infty}^\infty c_{k}$ is an absolutely convergent infinite series of complex numbers, and, for each real value $t$, let
>$$f(t) = \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}$$
>where $\omega_{k}=\frac{k}{p}$ and $p$ is some fixed positive number. Then $f$ is a continuous and periodic function with period $p$ whose complex exponential Fourier series is given by the above series. That is, for each integer $k$,
>$$c_{k} = \frac{1}{p}\int _{\text{period}} f(t)e^{-2 \pi \omega_{k}t} \, dt $$
>Moreover, if
>$$\sum_{k=-\infty}^\infty \lvert k^n c_{k} \rvert < \infty $$
>for some positive integer $n$, then $f$ is $n$-times differentiable, $f^{(n)}$ is continuous, and
>$$f^{(m)}(t)=\sum_{k=-\infty}^\infty c_{k}(i2\pi \omega_{k})^m e^{i 2 \pi \omega_{k}t}$$
>for $m=1,2,\dots ,n$

## Integrating Periodic Functions and Fourier Series

>[!theorem] Theorem Integration of Fourier Series ([[../../../PDFs/howell2016.pdf#page=215|Source]])
>Assume $f$ is a periodic, piecewise continuous function with period $p$ and
>$$\mathcal{FS}[f]|_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i 2\pi \omega_{k}t}$$
>Then, $\forall \tau \in\mathbb{R}$
>$$\sum_{\substack{k=-\infty\\k \neq 0}}^\infty \frac{c_{k}p}{i 2\pi k}e^{i2\pi \omega_{k}t}$$
>converges absolutely, and, for each pair of real numbers $a$ and $t$,
>$$\begin{align}
> \int _{a}^t f(\tau) \, d\tau &= \sum_{k=-\infty}^\infty \int _{a}^t c_{k}e^{i 2 \pi \omega_{k}\tau} \, d\tau  \\
> &= c_{0}[t-a] + \sum_{k=-\infty}^\infty \Gamma_{k}e^{i_{2} \pi \omega_{k}t}
>\end{align}$$
>where for $k \in \mathbb{Z}$
>$$\begin{align}
> \Gamma_{0}&= - \sum_{\substack{k=-\infty \\ k \neq 0}}^\infty  \frac{c_{k}p}{i 2\pi k}e^{i2\pi \omega_{k}ta} \\
> \Gamma_{k} &= \frac{c_{k}p}{i 2 \pi k}
>\end{align}$$
>
>Furthermore,
>$$\int _{a}^t f(\tau)\, d\tau - c_{0}[t-a] $$
>is a continuous, piecewise smooth, periodic function of $t$ with Fourier series
>$$\sum_{k=-\infty}^\infty \Gamma_{k}e^{i 2 \pi \omega_{k}t}$$
>>[!proof]
>>First, we proof absolute convergence
>>$$\begin{align}
>> \left\lvert  \frac{c_{k}p}{i 2\pi k}e^{i2\pi \omega_{k}t}  \right\rvert  &= \left\lvert  \frac{c_{k}}{k}  \right\rvert \frac{p}{2\pi}  \\
>>\end{align}$$
>>We estimate $\lvert c_{k} \rvert$ using [[#^79a237|estimation bounds for the coefficients]]
>>$$\begin{align}
>>\lvert c_{k} \rvert &= \left\lvert\frac{1}{p} \int _{\text{period}}  f(t)e^{-i 2\pi\omega_{k}t}   \, dt \right\rvert \\
>> &\leq \frac{1}{p}\int _{\text{period}} \lvert f(t) \rvert \, dt
>>\end{align}$$
>> Inserting this result gives 
>> $$\begin{align}
>>  \left\lvert  \frac{c_{k}p}{i 2\pi k}e^{i2\pi \omega_{k}t}  \right\rvert &\leq \frac{1}{\lvert k \rvert 2\pi }\int _{\text{period}} \lvert f(t) \rvert \, dt
>>\end{align}$$
>>