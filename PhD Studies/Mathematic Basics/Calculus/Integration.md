---
aliases: integration
---

>[!Theorem] Theorem Substitution Rule for Definite Integrals ([[../../../Sources/briggs2019.pdf#page=418|Source]])
> Let $u = g(x)$, where $g'$ is continuous on $[a,b]$ and let $f$ be continuous on the range of $g$. Then
> $$ \int_a^b f(g(x))g'(x) \,dx = \int_{g(a)}^{g(b)}f(u) \, du$$
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