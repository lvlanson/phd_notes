### 1.1 Basic Definitions 
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
>$$\hat{f}(t) = \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos(kt)+b_{k} \sin(kt)$$
>with
>$$\begin{align}
> a_{k} &= \frac{1}{\pi}\int _{-\pi}^\pi f(t)\cos(kt) \, dt \\
> b_{k} &= \frac{1}{\pi}\int _{-\pi}^\pi f(t)\sin(kt) \, dt 
>\end{align}$$

^da9999

>[!theorem] Theorem Generalized Fourier Transformation ([[../../../Sources/olson2017.pdf#page=34|Source]])
>Let $f \in L^2[-\pi, \pi ]$, then $f$ can be represented as the Fourier Series
>$$\hat{f}(t) = \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos\left( \frac{k\pi(t-h)}{H} \right)+b_{k} \sin\left( \frac{k\pi(t-h)}{H} \right)$$
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
>Let $f \in L^2[-T, T]$, then $f$ can be represented as the Fourier series
>$$\hat{f}(t)=\frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos\left( \frac{k\pi t}{T} \right) + b_{k} \sin\left( \frac{k\pi t}{T} \right)$$
>with 
>$$\begin{align}
> a_{k}&=\frac{1}{T} \int _{-T}^T f(t)\cos\left( \frac{k\pi t}{T} \right) \, dt \\
> b_{k}&= \frac{1}{T} \int _{-T}^T f(t)\sin\left( \frac{k\pi t}{T} \right) \, dt
>\end{align}$$

>[!def] Definition Partial Sum Approximation
>Let $f$ be the function to be approximated by a Fourier series. The partial sum approximation is given as a Fourier series with $n$ as its upper limit
>$$\begin{align}
>S_n\big(f(t)\big) &= \frac{a_{0}}{2} + \sum_{k=1}^n a_{k} \cos(kt)+b_{k} \sin(kt) \\
> &=\frac{a_{0}}{2} + \sum_{k=1}^n a_{k} \cos\left( \frac{k\pi(t-h)}{H} \right)+b_{k} \sin\left( \frac{k\pi(t-h)}{H} \right) \\
> &=\frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos\left( \frac{k\pi t}{T} \right) + b_{k} \sin\left( \frac{k\pi t}{T} \right)
>\end{align}$$
>with coefficients being defined as above

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
>>> If $f$ is even we have
>>> $$\int _{-T}^T f(t) \, dt = 2\int _{0}^T f(t) \, dt $$

^e42703

>[!property]
>The product of two functions being
>- even and even -> even
>- even and odd -> odd
>- odd and odd -> even

>[!def] Definition Characteristic Binary Function ([[../../../Sources/olson2017.pdf#page=36|Source]])
>$$\begin{align}
>\mathcal{X}_a(t) &= \begin{cases}
>1 & \text{ if } \lvert t \rvert< a \\
>0 & \text{ if } \lvert t \rvert > a
>\end{cases} \\
> \mathcal{X}_{[a,b]}(t) &= \begin{cases}
> 1 & \text{ if } t \in \left[ a,b \right] \\
> 0 & \text{ if } t \not\in [a, b] 
>\end{cases}
>\end{align}$$
>>[!remark]
>> If we write $\mathcal{X}(t)$ we consider $a = - \frac{\pi}{2}$ and $b = \frac{\pi}{2}$, i.e.
>> $$\mathcal{X}(t)=\mathcal{X}_{\left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]}(t)$$

>[!example] Example Calculating the Fourier Series for the Characteristic Binary Function
>Note, that $\mathcal{X}(t)$ is even and $\sin$ is odd, hence, their product is also odd and vanish under the integral. Therefore, we have
>$$\begin{align}
> b_{k} &= \frac{1}{\pi}\underbrace{ \int _{-\pi}^\pi \mathcal{X}(t)\sin(kt) \, dt }_{ =0 }  
>\end{align}$$ 
>We continue solving $a_k$. Here we separate it into the interesting intervals. Note, $\mathcal{X}$ will be $0$ if $t \not\in [-\frac{\pi}{2}, \frac{\pi}{2}]$, hence we split the integral for $a_k$, we have
>$$\begin{align}
> a_{k}&=\frac{1}{\pi} \int _{-\pi}^\pi \mathcal{X}(t)\cos\left( kt \right) \, dt\\
>    &=\frac{1}{\pi} \left( \underbrace{ \int _{-\pi/2}^{\pi /2} \mathcal{X}(t)\cos\left( kt \right) \, dt }_{ \substack{t \in[-{\pi}/{2}, {\pi} / {2}] \\ \mathcal{X}(t)=1} } + \underbrace{ \int _{|t|>\pi  /2} \mathcal{X}(t)\cos\left(kt \right) \, dt }_{ \substack{t \not\in[-{\pi}/{2}, {\pi} / {2} \\ =0}  } \right) \\
>    &= \frac{1}{\pi}\int _{-\pi/2}^{\pi /2} \cos\left( kt \right) \, dt  \\
>    &= \frac{1}{\pi}\left[\frac{1}{k}\sin(kt)\right]_{-\pi /2}^{\pi / 2} \\
>    &= \frac{1}{k\pi }\left(\sin \left( \frac{k\pi}{2} \right) -\sin \left( -\frac{k\pi}{2} \right) \right)
>\end{align}$$
>Note, since $\sin$ is odd, i.e. $\sin(t) = -\sin(-t)$ we can finish with
>$$a_{k} = \frac{2\sin\left( \frac{k\pi}{2} \right)}{k\pi}$$
>Further note, to solve $a_0$ we directly calculate it inside the integral, hence
>$$\begin{align}
> a_{0}&=\frac{1}{\pi} \int _{-\pi/2}^{\pi /2} \underbrace{ \mathcal{X}(t) }_{ =1 }\underbrace{ \cos\left( 0t \right)  }_{ =1 }\\
> a_{0}&=\frac{1}{\pi} \int _{-\pi/2}^{\pi /2} 1 \\
> a_{0}&=\frac{1}{\pi} \left[t\right]_{-\pi/2}^{\pi /2}\\
> a_{0}&=\frac{1}{\pi} \left(\frac{\pi}{2}+\frac{\pi}{2}\right)\\
> a_{0}&=1\\
>\end{align}$$
>We can give the Fourier series as
>$$\begin{align}
>f(t) &= \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos(kt)+b_{k} \sin(kt) \\
>     &= \frac{1}{2} + \sum_{k=1}^\infty \frac{2\sin \left( \frac{k\pi}{2} \right)}{k\pi} \cos(kt) \\
>\end{align}$$
>>[!note]
>> All odd $k$ will yield
>> $$\sin\left( \frac{k\pi}{2} \right)=\begin{cases}
>> 1 & k \text{ mod }4=1 \\
>> -1  &k\text{ mod } 4 =3 \\
>> 0 & \text{else}
>>\end{cases}$$
>>hence we can give the series as expanded form
>>$$\mathcal{X}(t)= \frac{1}{2}+ \frac{2}{\pi}\cos(t)-\frac{2}{3\pi}\cos(3t)+\frac{2}{5\pi}\cos(5t)-\frac{2}{7\pi}\cos(7t)\dots$$
>
>>[!code]-
>>```python
>>import sympy as sp
>>
>>def partial_sum(n: int):
>>	t = sp.symbols("t")
>>	approximation = 0.5
>>	for k in range(1, n):
>>		approximation += ((2 * sp.sin((k*sp.pi)/2))/(k*sp.pi))*sp.cos(k*t)
>>		
>>	return approximation
>>
>>p_10 = partial_sum(10) 
>>p_50 = partial_sum(50)
>>p_500 = partial_sum(500)  
>>```
>>![[figures/ex_1_p10.png]]
>>Figure: $S_{n}$ with $n=10$
>>![[figures/ex_1_p50.png]]
>>Figure: $S_{n}$ with $n=50$
>>![[figures/ex_1_p500.png]]
>>Figure: $S_{n}$ with $n=500$

>[!remark]
>Fourier series approximate functions only on the interval, but not outside the interval.

>[!def] Definition Error Function ([[../../../Sources/olson2017.pdf#page=42|Source]])
>$$E_{n}(f) = \int _{-\pi}^\pi \lvert f(t) - S_{n}(t) \rvert^2  \, dt $$

>[!remark]
>The approximation using the Fourier series has the property that
>$$\lim_{ n \to \infty } E_{n}(f) = 0$$

### 1.2 Orthogonality and Completeness

>[!def] Definition Inner Product ([[../../../Sources/olson2017.pdf#page=45|Source]])
>Let $f,g \in L^2[a,b]$, then the inner product between $f,g$ is
>$$(f \cdot g) \equiv \langle f,g \rangle = \int _{a}^b f(t)\overline{g(t)} \, dt $$
>The length of $f$ is given as
>$$\begin{align}
>\lvert\lvert f \rvert\rvert &= \sqrt{ \int _{a}^b \lvert f(t) \rvert^2  \, dt  } \\
>        &= \sqrt{ \langle f,f \rangle  }
>\end{align} $$

^a7fb8f

>[!def] Definition Orthogonality ([[../../../Sources/olson2017.pdf#page=46|Source]])
>1. The functions $f,g \in L^2[a,b]$ are orthogonal if
>$$\langle f,g \rangle =0$$
>2. A collection or set of functions $\{ o_{k}(t) \}_{k=0}^N$ is orthogonal if
>$$ \langle o_{j}, o_{i} \rangle= 0 \qquad \forall i\neq j$$
>3. A set of functions is orthonormal if they are orthogonal and $\lvert\lvert o_{j} \rvert\rvert = 1$

>[!theorem] Theorem Orthogonality of Sine and Cosine Functions ([[../../../Sources/olson2017.pdf#page=46|Source]])
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

>[!proof]- Proof Correctness of $a_k$ and $b_k$ for the Fourier Series
>>We proof the correctness of the coefficients $a_k$ and $b_k$ of the [[#^93ee52| Generalized Fourier Series]] and the [[#^da9999| Fourier Series]].
>
>Using the [[#^da9999 | Fourier series]] of $f$ in the following inner product, we have
>$$\begin{align}
>\langle f(t), \cos(jt) \rangle  &= \int _{-\pi}^\pi f(t) \cos(jt) \, dt \\
>                    &=\int _{-\pi}^\pi  \underbrace{ \left( \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k}\cos(kt)+b_{k}\sin(kt) \right) }_{ \text{Fourier series of $f$} } \cos(jt)\, dt \\
>                    &= \underbrace{ \int _{-\pi}^\pi  \frac{a_{0}}{2}\cos(jt)\,  dt }_{ =0 \substack{ \text{ because} \\ \;\;\;\;\sin(\pm\pi) = 0}} +  \underbrace{\sum_{k=1}^\infty \int _{-\pi}^\pi a_{k}\cos(kt)\cos(jt) }_{ =\begin{cases}
>0 & \text{ if } j \neq k \\
>\pi a_{k} & \text{ if } j = k 
>\end{cases} } \, dt + \underbrace{ \int _{-\pi}^\pi b_{k} \sin(kt) \cos(jt) \, dt  }_{ =0 }  \\
>&= a_{k}\pi
>\end{align}$$
> Hence, we have
> $$\begin{align}
> \pi a_{k} &= \int _{-\pi}^\pi f(t) \cos(kt) \, dt \\
> a_{k} &= \frac{1}{\pi}\int _{-\pi}^\pi f(t) \cos(kt) \, dt 
>\end{align}$$
>>[!note]
>>We exploited the property of the scalar product, that the estimation of $f(t)$ by the Fourier series is a composition of $\sin$ and $\cos$ terms, where all terms cancel out due to orthogonality except for the case where $k=j$. Therefore, we can determine each $k$-th term precisely.
>
>
> Similarly, for $\sin$ we get
> $$\begin{align}
> \langle f(t), \sin(jt) \rangle &= \int _{-\pi}^\pi f(t) \sin(jt) \, dt \\ \\
> &=\int _{-\pi}^\pi  \underbrace{ \left( \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k}\cos(kt)+b_{k}\sin(kt) \right) }_{ \text{Fourier series of $f$} } \sin(jt)\, dt \\
> &= \underbrace{ \int _{-\pi}^\pi  \frac{a_{0}}{2}\sin(jt)\,  dt }_{ =0 \text{ sin is odd} }  +  \underbrace{\sum_{k=1}^\infty \int _{-\pi}^\pi a_{k}\cos(kt)\sin(jt) \, dt}_{ = 0 }  + \underbrace{ \int _{-\pi}^\pi b_{k} \sin(kt) \sin(jt) \, dt  }_{ =\begin{cases}
>0 & \text{ if } j \neq k \\
>\pi b_{k} & \text{ if } j = k 
>\end{cases}  }  \\
>&= \pi b_{k}
>\end{align}$$
> Hence, we have
> $$\begin{align}
> \pi b_{k} &= \int _{-\pi}^\pi f(t) \sin(kt) \, dt \\
> b_{k} &= \frac{1}{\pi}\int _{-\pi}^\pi f(t) \cos(kt) \, dt \tag*{$\square$}
>\end{align}$$

>[!remark] Remark Length of $\sin$ and $\cos$ in $L^2[-T,T]$
>Let $(L^2[-T,T], \lvert\lvert \cdot \rvert\rvert)$ as stated in the [[#^a7fb8f| inner product]]
>1. $\lvert\lvert \sin \rvert\rvert = \sqrt{T }$
>2. $\lvert\lvert \cos \rvert\rvert = \sqrt{T }$
>
>>[!note] Note Change of Variables
>> To properly show this, we need a change of variables which is used in Fouries series. Consider a function $f$ to be represented on a compact interval $[-T, T]$. By the property of the Fourier series to be periodic, we can conclude that the given Fourier series representation $\hat{f}(t)$ will be periodic on the interval $[-T,T]$, hence we require the periodicity of $\hat{f}(t)$ to match the length of the given interval, which is $2T$.
>>
>>We introduce the frequency parameter $\omega$ controlling the oscillation factor of the trigonometric functions. Note, the standard $\sin$ and $\cos$ are $2\pi$ periodic, which means a period is closed under the interval $[-\pi, \pi]$.  Therefore, $\omega=1$ in
>>$$\begin{align}
>> \sin(\omega x) \\
>> \cos(\omega x)
>>\end{align}$$
>>We have the relation
>>$$\begin{align}
>> \frac{2\pi}{\omega}&= \underbrace{ 2\pi }_{ \substack{\text{Length of}\\ \text{the period}}} \\
>> \omega &= 1 
>>\end{align}$$
>>Now, if we want to change the period from $[-\pi, \pi]$ to $[-T, T]$, we have do adjust $\omega$ such that the following condition holds
>>$$\begin{align}
>> \frac{2\pi}{\omega}&= \underbrace{ 2T }_{ \substack{\text{Length of}\\ \text{the period}}} \\ 
>> \omega &= \frac{\pi}{T}
>>\end{align}$$
>>If we state $$\begin{align}
>> \sin \left( \frac{\pi}{T}x \right) \\
>> \cos \left( \frac{\pi}{T}x \right)
>>\end{align}$$
>>the functions are guaranteed to perfectly close the period on the interval $[-T,T]$. This change of variable makes it possible to determine the length of the trigonometric functions on the more general interval by introducing $\omega$.
>>
>>The parameter $\omega$ can therefore easily be determined if you consider the period $P$ being half the length of the interval. Then we have
>>$$\omega =\frac{\pi}{P}$$
>>
>
>>[!proof]-
>>1. Note, we have $\omega=\frac{\pi}{T}$  for $\sin(\omega t)$
>>$$\begin{align}
>>\lvert\lvert \sin \rvert\rvert &= \sqrt{ \int _{-T}^T  \left\lvert  \sin\left( \frac{\pi t}{T} \right)  \right\rvert^2 \, dt }  \\
>> &= \sqrt{ \int _{-T}^T \sin^2\left( \frac{\pi t}{T} \right)  \, dt  } \\
>> &= \sqrt{ \int_{-T}^T \frac{1 - \cos\left( \frac{2\pi t}{T} \right)}{2} \, dt }\\
>> &= \sqrt{\frac{1}{2} \int_{-T}^T 1-\cos\left( \frac{2\pi t}{T} \right) \, dt } \\
>> &= \sqrt{ \frac{1}{2} \left[t-\frac{\sin\left( \frac{2\pi t}{T} \right)T}{2\pi}\right]_{-T}^T  } \\
>> &= \sqrt{ \frac{1}{2} \left(T-\frac{\sin\left( \frac{2\pi \cancel{ T }}{\cancel{ T }} \right)T}{2\pi} - \left( -T-\frac{\sin\left( \frac{-2\pi \cancel{ T }}{\cancel{ T }} \right)T}{2\pi} \right)\right)  }\\
>> &= \sqrt{ \frac{1}{2} \left(T  \underbrace{- \frac{\sin(2\pi)T}{2\pi} }_{ =0 }  + T  \underbrace{+ \frac{\sin(-2\pi)T}{2\pi} }_{ =0 }  \right)  } \\
>> &= \sqrt{ \frac{1}{2} \left(2T\right)  } \\
>> &= \sqrt{ T  } \\
>>\end{align}$$
>>2. Note, we have $\omega=\frac{\pi}{T}$ for $\cos(\omega  t)$
>>$$\begin{align}
>> \lvert\lvert \cos \rvert\rvert &= \sqrt{ \int _{-T}^T \lvert \cos\left(\frac{\pi t}{T}\right) \rvert^2 \, dt  } \\
>>  &= \sqrt{ \int _{-T}^T \cos^2\left(\frac{\pi t}{T}\right) \, dt  } \\
>>  &= \sqrt{ 2\int _{0}^T \cos^2\left(\frac{\pi t}{T}\right) \, dt  } \tag{1} \\ 
>>  &= \sqrt{ 2\left[\frac{1}{2}\left(\cos\left(\frac{\pi t}{T}\right)\sin\left(\frac{\pi t}{T}\right) + t\right)\right]_{0}^T } \\
>>  &= \sqrt{ \cos(\pi)\underbrace{ \sin(\pi) }_{ =0 } + T } \\  
>>  &= \sqrt{ T }
>>\end{align}$$
>> Note in equation $(1)$ we made use of the fact that $\cos$ is an [[#^e42703 | even function]], i.e. $\int _{-T}^T \cos(t)\, dt = 2\int _{0}^T \cos(t)\, dt$

