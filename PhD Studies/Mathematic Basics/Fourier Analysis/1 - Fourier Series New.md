
>[!def] Definition Trigonometric Fourier Series ([[../../../PDFs/howell2016.pdf#page=113|Source]])
>Let $f$ be a periodic function with period $p$ where $p$ is some positive number. The (trigonometric) Fourier $FS$ series for $f$ is the infinite series
>$$FS[f]\rvert_{t} = A_{0} + \sum_{k=1}^\infty \Big[ a_{k} \cos\big(2\pi \omega_{k}t\big) + b_{k} \sin\big(2\pi \omega_{k}t\big)\Big]$$
>where, for $k = 1,2,3, \dots$
>$$\begin{align}
> \omega_{k} &= \frac{k}{p} \tag{Frequency Coefficient}\\
> A_{0} &= \frac{1}{p} \int _{0}^p f(t) \, dt \tag{Trigonometric Coefficient}\\
> a_{k} &= \frac{2}{p} \int _{0}^p f(t) \cos(2\pi \omega_{k}t) \, dt \tag{Trigonometric Coefficient}\\
> b_{k} &= \frac{2}{p} \int _{0}^p f(t) \sin(2\pi \omega_{k}t) \, dt \tag{Trigonometric Coefficient}\\
>\end{align}$$

>[!lemma] 
>If $f$ is either a constant function, a sine function or a cosine function, then
>$$FS[f]|_{t} = f(t)$$
>Especially,
>$$FS[0]|_{t} = 0$$
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
>>FS[f]|_{t}  &= \underbrace{ A_{0} }_{ =c } + \sum_{k=1}^\infty \Big[ \underbrace{ a_{k} }_{ =0 } \cos\big(2\pi \omega_{k}t\big) + \underbrace{ b_{k} }_{ =0 } \sin\big(2\pi \omega_{k}t\big)\Big] \\
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