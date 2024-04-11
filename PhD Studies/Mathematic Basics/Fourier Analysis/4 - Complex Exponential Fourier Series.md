>[!def] Definition Complex Exponential Fourier Series ([[../../../PDFs/howell2016.pdf#page=157|Source]])
> Let $f$ be a periodic function with period $p$. The _complex exponential Fourier series_ for $f$ denoted by $\mathcal{F}[f]|_{t}$ is the infinite series
> $$\sum_{k=-\infty}^\infty c_{k}e^{i 2 \pi \omega_{k}t}$$
> with
> $$\omega_{k}=\frac{k}{p} \tag{$k=1,2,3,\dots$}$$
> and
> $$c_{k}=\frac{1}{p} \int f(t)e^{-i2\pi \omega_{k}t} \, dt $$

>[!remark]- Deriving the Complex Exponential Form of the Fourier Series ([[../../../PDFs/howell2016.pdf#page=155|Source]])
>Let $f$ be a periodic, piecewise continuous function with period $p$ and the trigonometric Fourier series
>$$\mathcal{F}[f]|_{t} = A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) + b_{k}\sin(2\pi \omega_{k}t)\Big] \tag{1}$$
>We use the following identities
>$$\begin{align}
> \cos(2 \pi \omega_{k}t)  &= \frac{e^{i2\pi \omega_{k}t}+ e^{-i2\pi \omega_{k}t}}{2} \\
> \sin(2 \pi \omega_{k}t)  &= \frac{e^{i2\pi \omega_{k}t}- e^{-i2\pi \omega_{k}t}}{2i}
>\end{align}$$
>>[!note]- Deriving the Identities ([[../../../PDFs/howell2016.pdf#page=157|Source]])
>>We use the [[../Complex Analysis/Fundamental Properties|Euler form]] definition of the complex number $\cos \theta + i \sin \theta$ 
>>$$\begin{alignat}{2}
>>  e^{i\theta} &= \cos (\theta) + i \sin (\theta) \tag{1}\\
>>  e^{-i\theta} &= \cos(-\theta) + i \sin(- \theta) \tag{2}\\
>>  &= \cos(\theta)- i \sin(\theta) \tag{Even and Odd Function}
>>\end{alignat}$$
>>Combining these functions yields
>>$$\begin{alignat}{2}
>> e^{i\theta} + e^{-i\theta} &= 2\cos(\theta) \qquad&&\Big\vert :2 \tag*{$(1) + (2)$} \\
>> \cos(\theta) &= \frac{e^{i\theta} + e^{-i\theta}}{2}  \tag*{$\checkmark$}\\
>> e^{i\theta} - e^{-i\theta} &= 2i \sin(\theta) \qquad&&\Big\vert :2i \tag*{$(1) - (2)$} \\
>> \sin(\theta) &= \frac{e^{i\theta} - e^{-i\theta}}{2i} \tag*{$\checkmark$}
>>\end{alignat}$$
>
>Having determined these identities, we can insert these into equation $(1)$ 
>$$\begin{align}
> \mathcal{F}[f]|_{t} &= A_{0} + \sum_{k=1}^\infty\left[a_{k}  \frac{e^{i2\pi \omega_{k}t}+ e^{-i2\pi \omega_{k}t}}{2} + b_{k} \frac{e^{i2\pi \omega_{k}t}- e^{-i2\pi \omega_{k}t}}{2i}\right] \\ 
> &= A_{0} + \sum_{k=1}^\infty\left[  \frac{a_{k}e^{i2\pi \omega_{k}t}+ a_{k}e^{-i2\pi \omega_{k}t}}{2} + \underbrace{ \frac{b_{k} e^{i2\pi \omega_{k}t}- b_{k} e^{-i2\pi \omega_{k}t}}{2i} }_{ \text{expand with } i^3} \right]  \\[1em]
> &= A_{0} + \sum_{k=1}^\infty\left[  \frac{a_{k}e^{i2\pi \omega_{k}t}+ a_{k}e^{-i2\pi \omega_{k}t}}{2} +\frac{-ib_{k} e^{i2\pi \omega_{k}t}+i b_{k} e^{-i2\pi \omega_{k}t}}{2} \right]  \\ 
> &= A_{0} + \sum_{k=1}^\infty\left[  \frac{a_{k}e^{i2\pi \omega_{k}t}-ib_{k} e^{i2\pi \omega_{k}t} + a_{k}e^{-i2\pi \omega_{k}t} +i b_{k} e^{-i2\pi \omega_{k}t}}{2} \right]\\
> &= A_{0} + \sum_{k=1}^\infty\left[  \frac{a_{k}e^{i2\pi \omega_{k}t}-ib_{k} e^{i2\pi \omega_{k}t}}{2} + \frac{a_{k}e^{-i2\pi \omega_{k}t} +i b_{k} e^{-i2\pi \omega_{k}t}}{2} \right]\\
> &= A_{0} + \sum_{k=1}^\infty\left[  \underbrace{ \frac{a_{k}-ib_{k} }{2} }_{ =C_{k} }e^{i2\pi \omega_{k}t} + \underbrace{ \frac{a_{k} +i b_{k} }{2} }_{ =D_{k} }e^{-i2\pi \omega_{k}t} \right]\\
> &= A_{0} + \sum_{k=1}^\infty\Big[C_{k}e^{i2\pi \omega_{k}t} + D_{k} e^{-i2\pi \omega_{k}t}\Big] \\
> &= A_{0} + \sum_{k=1}^\infty C_{k}e^{i2\pi \omega_{k}t} + \sum_{k=1}^\infty D_{k}e^{i2\pi \omega_{k}t} \tag{1}
>\end{align}$$
> We will now reshape the equation by expanding the domain of the $k$'s, i.e. $k \in \mathbb{Z}$. Therefore, lets define the following coefficient
> $$c_{k} = \begin{cases}
> C_{k} & \text{ if } k = 1,2,3,\dots \\
> A_{0} & \text{ if } k = 0 \\
> D_{-k} & \text{ if } k = -1, -2, -3,\dots
>\end{cases}$$
>We will now use these coefficients to justify the exponential Fourier series
>$$\sum_{k=-\infty}^\infty c_{k}e^{2i\pi \omega_{k}t}$$
>>[!note] Justification for the Coefficients
>>Case $A_0$
>>> $$\begin{align}
>>> c_{0} &= A_{0}e^{2i\pi \omega_{0}t}\\
>>> &= A_{0}e^{2i\pi \frac{0}{p}t} \\
>>> &= A_{0}e^{0} \\
>>> &= A_{0} \tag*{$\checkmark$}
>>>\end{align}$$
>>
>>Case $D_{-k}$
>>>$$\begin{align}
>>> \sum_{k=1}^{\infty}D_{k}e^{-2i\pi \omega_{k}t} &=  \sum_{k=1}^{\infty}D_{k}e^{2i\pi \omega_{-k}t} \\
>>> &= \sum_{n=-1}^{-\infty}D_{-n}e^{2i\pi \omega_{n}t} \tag{change of variable} \\
>>> &= \sum_{k=-1}^{-\infty}c_{k}e^{2i\pi \omega_{k}t} \tag{renaming}
>>>\end{align}$$
>>
>>Case $C_k$
>>> This case is rather obvious
>>> $$\begin{align}
>>> \sum_{k=1}^\infty C_{k}e^{2i\pi \omega_{k}t} = \sum_{k=1}^\infty c_{k}e^{2i\pi \omega_{k}t}
>>>\end{align}$$
>>
>>Hence, piecing the results together
>>$$\begin{align}
>> \mathcal{F}[f]|_{t} &= c_{0} + \sum_{k=-1}^{-\infty}c_{k}e^{2i\pi \omega_{k}t} + \sum_{k=1}^{\infty}c_{k}e^{2i\pi \omega_{k}t} +  \sum_{k=1}^\infty c_{k}e^{2i\pi \omega_{k}t} \\
>>  &= \sum_{k=-\infty}^\infty c_{k}e^{2i\pi \omega_{k}t}
>>\end{align}$$

>[!remark] Deriving the Coefficients $c_k$ of the Complex Exponential Form ([[../../../PDFs/howell2016.pdf#page=157|Source]])
>According to the [[3 - Inner Products, Norms and Orthogonality#^3f9bbe| theorem on orthogonal expansions]], we can define the coefficients of the expansion by using 
>$\phi_{k} = \,e^{i 2\pi \omega_{k}t}$
>$$\begin{align}
> c_{k} &= \frac{\left\langle f\,,\,e^{i 2\pi \omega_{k}t} \right\rangle}{\lvert\lvert e^{i 2\pi \omega_{k}t} \rvert\rvert^2 }  \\
> &= \frac{1}{p} \int _{0}^p f(t)e^{-i 2\pi \omega_{k}t} \, dt 
>\end{align}$$

>[!property] Property Inner Product with Exponential Representation  ([[../../../PDFs/howell2016.pdf#page=157|Source]])
>Let $g$ be any periodic, piecewise continuous function with period $p$ with $n \in \mathbb{Z}$, then
>$$\begin{align}
> \left\langle g(t)\,,\,e^{i_{2}\pi \omega_{n}t} \right\rangle &= \int _{0}^p g(t)\left(e^{i_{2}\pi \omega_{n}t}\right)^* \, dt   \\
> &= \int _{0}^p g(t)e^{-i_{2}\pi \omega_{n}t} \, dt
>\end{align}$$

>[!property] Property Exponential Representations form an Orthogonal Set ([[../../../PDFs/howell2016.pdf#page=157|Source]])
>Let $k,n \in \mathbb{Z}$ with $k\neq n$ then 
>$$e^{i2\pi \omega_{k}t} \text{ and } e^{i2\pi \omega_{n}t} $$
>are orthogonal
>>[!proof]-
>>$$\begin{align}
>> \left\langle e^{i2\pi \omega_{k}t}\,,\,e^{i2\pi \omega_{n}t} \right\rangle &= \int _{0}^p e^{i2\pi \omega_{k}t}e^{i2\pi \omega_{n}t} \, dt \\
>> &= \int _{0}^p \exp\left( \frac{i 2\pi(k-n)}{p}t \right)  \, dt \tag*{$\left(\omega_{k} = \frac{k}{p}\right)$} \\
>> &= \left[ \frac{p}{i2\pi(k-n)} \exp\left( \frac{i 2\pi(k-n)}{p}t \right)  \right]_{0}^p \tag{Solving Integral} \\
>> &= \frac{p}{i2\pi(k-n)} \left[ \exp\left( \frac{i 2\pi(k-n)}{p}t \right)  \right]_{0}^p \\
>> &= \frac{p}{i2\pi(k-n)} \left( \underbrace{ e^{i2\pi(k-n)} }_{ =1 } - e^0  \right) \\
>> &= \frac{p}{i2\pi(k-n)} \left(1-1 \right) \\
>> &= 0 \\
>>\end{align}$$
>>where we used for $e^{i2\pi(k-n)}$ the [[../Complex Analysis/Fundamental Properties#^45ef91|special identity]] of Euler's formula.
