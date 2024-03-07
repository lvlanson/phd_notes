>[!def] Trivial Discontinuities/Removable Discontinuities ([[../../../PDFs/howell2016.pdf#page=29|Source]])
>The function $f$ has a trivial discontinuity at $x_{0}$ if the limit does exist as $x$ approaches $x_{0}$ but either this limit does not equal $f(x_{0})$ or $f(x_{0})$ does not exist according to the definition of the given function.
>
>Such a discontinuity can be removed by setting  $$$\lim_{ x \to x_{0} }f(x)=f(x_{0})$$
>at its discontinuous point.
>>[!example]
>>$$\text{sinc}(x) = \frac{\sin(x)}{x} $$
>>is not defined for $x=0$, but its limit exist using L'Hospitals rule
>>$$\begin{align}
>> \lim_{ x \to 0 } \frac{\sin(x)}{x} &= \lim_{ x \to 0 } \frac{\frac{d}{dx} \sin(x)}{\frac{d}{dx}x} \\
>> &= \lim_{ x \to 0 } \frac{\cos(x)}{1} = 1 
>>\end{align}$$
>
>>[!example] Fix for Example
>> We redefine the function, such that $\lim_{ x \to x_{0} }f(x)=f(x_{0})$. For our example we get
>> $$\text{sinc}(x) = \begin{cases}
>> \dfrac{\sin(x)}{x} &\text{ if } x \neq 0 \\
>> 1 & \text{ if } x = 0
>>\end{cases}$$

>[!def] Jump Discontinuities ([[../../../PDFs/howell2016.pdf#page=30|Source]])
>A function $f$ has a jump discontinuity if the left- and right-hand limits of the function at $x_{0}$ both exist but are not equal, i.e.
>$$\lim_{ x \to x_{0}^- } f(x) \neq \lim_{ x \to x_{0}^+ } f(x) $$
>A jump discontinuity can be fixed by adding a middle point in the jump, i.e.
>$$f(x_{0})= \frac{1}{2} \Bigg[\lim_{ x \to x_{0}^+ } f(x)+ \lim_{ x \to x_{0}^- }f(x)\Bigg]$$

>[!def] "Bad Discontinuities"  ([[../../../PDFs/howell2016.pdf#page=31|Source]])
>If $f$ is neither jump discontinuous nor trivial discontinuous then we will consider it to be bad discontinuous.
>>[!example]
>>![[figures/discontinuities.png]]