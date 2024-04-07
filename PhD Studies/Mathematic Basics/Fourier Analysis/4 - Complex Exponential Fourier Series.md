>[!remark] Deriving the Exponential Form of the Fourier Series
>Let $f$ be a periodic, piecewise continuous function with period $p$ and the trigonometric Fourier series
>$$\mathcal{F}[f]|_{t} = A_{0} + \sum_{k=1}^\infty \Big[a_{k} \cos(2\pi \omega_{k}t) + b_{k}\sin(2\pi \omega_{k}t)\Big] \tag{1}$$
>We use the following identities
>$$\begin{align}
> \cos(2 \pi \omega_{k}t)  &= \frac{e^{i2\pi \omega_{k}t}+ e^{-i2\pi \omega_{k}t}}{2} \\
> \sin(2 \pi \omega_{k}t)  &= \frac{e^{i2\pi \omega_{k}t}- e^{-i2\pi \omega_{k}t}}{2i}
>\end{align}$$
>>[!note]- Deriving the Identities
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
> &= A_{0} + \sum_{k=1}^\infty\left[C_{k}e^{i2\pi \omega_{k}t} + D_{k} e^{-i2\pi \omega_{k}t}\right]
>\end{align}$$
