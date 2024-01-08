---
aliases: integration
---

>[!Theorem] Theorem Substitution Rule for Definite Integrals ([[../../../Sources/briggs2019.pdf#page=418|Source]])
> Let $u = g(x)$, where $g'$ is continuous on $[a,b]$ and let $f$ be continuous on the range of $g$. Then
> $$ \int_a^b f(g(x))g'(x) \,dx = \int_{g(a)}^{g(b)}f(u) \, du$$
>>[!note]-
>>The substitution rule reverses the chain rule of derivation
>
>>[!example]- Example $\int_0^2 \frac{1}{(x+3)^3} \, dx$
>>First we identify from the definition
>>$$\begin{align}
>>g(x) &= x+3 \\
>>g'(x) &= 1 \\
>>f(g(x)) &= \frac{1}{g(x)^3} \\
>>&= \frac{1}{(x+3)^3}
>>\end{align}$$
>>After having identified all components, we can denote $$\begin{align} u &= x+ 3\\ du &= dx \end{align}$$
>>Because we have changed the variables, we also need to take care of the limits of the definite integral
>>$$\begin{align}
>>g(a) = g(0) &= 3 \\
>>g(b) = g(2) &= 5
>>\end{align}$$
>>Hence, we have by substitution
>>$$\begin{align}
>> \int_0^2 \frac{1}{(x+3)^3} \, dx &= \int_3^5 \frac{1}{(u)^3} \, du \\
>> 							   &= \int_3^5 (u)^{-3} \, du \\
>> 							   &= -\frac{u^{-2}}{2} \;\Bigg\vert_{3}^5 \\
>> 							   &= -\frac{1}{2u^2} \;\Bigg\vert_{3}^5 \\
>> 							   &= \frac{1}{2\cdot 5^2} - \frac{1}{2 \cdot 3^2}  \\
>> 							   &= \frac{8}{225}
>>\end{align}$$
>>
>
>>[!example]- Example $\int_2^3 \frac{x^2}{x^3 - 7} \, dx$
>>Again we identify the functions from the definition
>>$$\begin{align}
>>g(x) &= x^3 -7 \\
>>g'(x) &= 3x^2 \\
>>f(g(x)) &= \frac{\frac{1}{3}}{g(x)} \\
>>&= \frac{1}{3g(x)}
>>\end{align}$$
>>After having identified all components, we can denote 
>>$$\begin{align} 
>>u &= x^3 - 7\\ 
>>du &= dx \end{align}$$
>>Because we have changed the variables, we also need to take care of the limits of the definite integral
>>$$\begin{align}
>>g(a) = g(2) &= 1 \\
>>g(b) = g(3) &= 20
>>\end{align}$$
>>Hence, we have by substitution
>>$$\begin{align}
>> \int_2^3 \frac{x^2}{x^3-7} \, dx &= \int_1^{20} \frac13 u^{-1} \, du \\
>> 							     &= \frac13 \int_1^{20}  u^{-1} \, du \\
>> 							     &= \frac13 \Bigg(\ln |u| \;\Bigg\vert^{20}_1\Bigg) \\
>> 							     &= \frac13 \left( \ln 20 - \ln 1\right) \\
>> 							     &= \frac13 \ln 20  \\
>> 							     &\approx 0.999  \\
>>\end{align}$$
>
>^thmSubstitutionRule


>[!Theorem] Theorem Integration by Parts ([[../../../Sources/briggs2019.pdf#page=550|Source 1]], [[../../../Sources/zotero-182.pdf#page=270|Source 2]])
> Let $u = f(x)$ and $v=g(x)$ be functions with continuous derivatives. The integration by parts formula for the given two functions can be formulated as
> $$ \int u\, dv \, = uv - \int v \,du  $$
>>[!proof]-
>>Let $h(x) = f(x)g(x)$. Using the product rule we have
>>$$ h'(x) = f'(x)g(x)+ g'(x)f(x)$$
>>Integrating both sides gives
>>$$ \int h'(x) \, dx = \int  g(x) f'(x) \, dx + \int  f(x) g'(x)\, dx $$ 
>>Now we solve for $\int f(x)g'(x) dx$
>>$$ \int f(x)g'(x)  \, dx = f(x)g(x) - \int g(x)f'(x) \, dx $$ 
>>Making the substitution 
>>$$\begin{align}
>> u &= f(x) \\
>> v &=g(x) \end{align}$$
>> and the resulting
>> $$\begin{align}
>> du &= f'(x) \\
>> dv &= g'(x) \end{align}$$
>> gives the resulting formula and concludes the proof <p style="text-align: right">$\square$</p>
>
>>[!note]-
>>1. The integration by parts reverses the product rule.
>>2. The complete formula looks like $$\int f(x)\, \frac{dg(x)}{dx} dx \, = f(x)g(x) - \int g(x) \frac{df(x)}{dx} dx$$
>
>>[!example]- Example $\int  x \sin (x) \, dx$  ([[../../../Sources/zotero-182.pdf#page=270|Source]])
>>We choose 
>>$$\begin{align}
>> u & = x \\
>> dv  & = \sin (x)
>>\end{align}$$
>>Then we can determine
>>$$\begin{align}
>> du &= 1 \\
>> v &= \int \sin x \, dx \\
>>   &= -\cos x 
>>\end{align}$$
>>Hence, we have
>>$$\begin{align}
>>\int  x \sin (x) \, dx &= \underbrace{ (x) }_{ =u }\underbrace{ (-\cos x) }_{ =v } - \int \underbrace{ \cos x }_{ =dv } \, \cdot \underbrace{ 1 }_{ =du }dx \\ \\
>> &= -x \cos x + \int \cos x \, dx \\ \\
>> &= -x\cos x + \sin x + c
>>\end{align}$$
>
>>[!example]- Example $\int \frac{\ln x}{x^3} \,dx$ ([[../../../Sources/zotero-182.pdf#page=272|Source]])
>>We rewrite as
>>$$\int \frac{\ln x}{x^3} \,dx = \int x^{-3} \ln x \, dx $$
>>Now we choose
>>$$\begin{align}
>> u &= \ln x \\
>> dv &= x^{-3}
>>\end{align}$$
>>We determine
>>$$ \begin{align}
>>du &= \frac{1}{x} \\
>> v &= \int x^{-3} \, dx \\
>> &=-\frac{1}{2}x^{-2}
>>\end{align}$$
>>Now we plug-in into the formula
>>$$\begin{align}
>> \int u\, dv \, &= uv - \int v \,du \\ \\
>>           &=  -\frac{1}{2}x^{-2}\ln x - \int -\frac{1}{2}x^{-2} \frac{1}{x} \, dx \\
>>           &=  -\frac{1}{2}x^{-2}\ln x + \frac{1}{4}x^{-2}  + c \\
>>           &= x^{-2}\left(\frac{1}{4}-\frac{1}{2}\ln x \right) + c
>>\end{align}$$
>^thmIntByParts