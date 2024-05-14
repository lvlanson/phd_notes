>[!def] Definition Periodic Extension ([[../../../PDFs/howell2016.pdf#page=121|Source]])
>Let $f$ be a piecewise continuous function defined on the domain $(0,L)$. A periodic function $\widehat{f}$ with period $L$ is called **periodic extension of** $f$ if 
>$$f\Big|_{(0,L)} = \widehat{f}\Big|_{(0,L)}$$

>[!def] Definition Basic Periodic Extension ([[../../../PDFs/howell2016.pdf#page=121|Source]])
>Let $\widehat{f}$ be the periodic extension of $f$ over $(0,L)$ with period $p=L$ and
>$$\widehat{f}(t)=\begin{cases}
f(t) & \text{ if } 0 < t < L \\
\widehat{f}(t-L) & \text{ else }
\end{cases}$$
>>[!pic]- Illustration
>>![[figures/basic_periodic_extension.png | center ]]

>[!def] Definition Odd Periodic Extension ([[../../../PDFs/howell2016.pdf#page=121|Source]])
> Let $f_{0}$ be the **odd function** 
> $$f_{0}(t) = \begin{cases}
> f(t) & \text{ if } 0 < t < L \\
> -f(-t) & \text{ if } -L < t < 0
>\end{cases}$$
>with period $p=2L$. Then the **odd periodic extension** $\widehat{f_{0}}$ can be given as
>$$\widehat{f}(t) = \begin{cases}
>f(t) & \text{ if } 0 < t < L \\
>-f(-t) & \text{ if } -L < t < 0 \\
>\widehat{f_{0}}(t-2L) & \text{ else} \\
>\end{cases}$$
>>[!pic] Illustration
>>![[figures/periodic_odd_extension.png]]

>[!Lemma] Lemma Sine Fourier Series ([[../../../PDFs/howell2016.pdf#page=135|Source]])
>Let $\widehat{f}$ be an odd periodic extension of $f$ with period length $p=2L$. Then the Fourier series of $\widehat{f}$ is called the **sine Fourier series** and can be given as
>$$\mathcal{FS}[\widehat{f}]|_{t} = \sum_{k=1}^\infty \sin(2\pi \omega_{k}t)$$
>with 
>$$b_{k}=\frac{2}{L}\int _{0}^{L} \widehat{f}_{0}(t) \sin\left( \frac{\pi k}{L}t \right) \, dt $$
>>[!proof]-
>> This is an immediate consequence of the [[1 - Classical Fourier Series#^3277d9| Fourier series for odd functions]].


>[!def] Definition Even Periodic Extension
> Let $f_{0}$ be the **even function** 
> $$f_{0}(t) = \begin{cases}
> f(t) & \text{ if } 0 < t < L \\
> f(-t) & \text{ if } -L < t < 0
>\end{cases}$$
>with period $p=2L$. Then the **even periodic extension** $\widehat{f_{0}}$ can be given as
>$$\widehat{f}(t) = \begin{cases}
>f(t) & \text{ if } 0 < t < L \\
>f(-t) & \text{ if } -L < t < 0 \\
>\widehat{f_{0}}(t-2L) & \text{ else} \\
>\end{cases}$$
>>[!pic] Illustration
>>![[figures/periodic_even_function.png]]


>[!lemma] Lemma Cosine Fourier Series ([[../../../PDFs/howell2016.pdf#page=137|Source]])
>Let $\widehat{f}$ be an even periodic extension of $f$ with period length $p=2L$. Then the Fourier series of $\widehat{f}$ is called the **cosine Fourier series** and can be given as
>$$\mathcal{FS}[\widehat{f}]|_{t} = A_{0} + \sum_{k=1}^\infty a_{k} \cos\left( \frac{k\pi}{L}t \right)$$
>with
>$$\begin{align}
> A_{0}&= \frac{1}{L} \int_{0}^L f(t) \, dt \\
> a_{k} &= \frac{2}{L}\int_{0}^L f(t) \cos\left( \frac{k\pi}{L}t \right)\, dt  
>\end{align}$$
>>[!proof]-
>>This is an immediate consequence of the [[1 - Classical Fourier Series#^7e4728| Fourier series for even functions]].