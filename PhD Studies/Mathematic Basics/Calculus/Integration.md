>[!def] Definition Partition ([[../../../PDFs/zotero-182.pdf#page=18|Source]])
>A set of point $P=\{ x_{i} \}$ for $i=0,1,2,\dots,n$ with $a=x_{0}<x_{1}<x_{2}<\dots<x_{n}=b$, which divides the interval $[a,b]$ into subintervals of the form $[x_{0},x_{1}], [x_{1},x_{2}], \dots, [x_{n-1}, x_{n}]$ is called a **partition** of $[a,b]$.
>
>If the subintervals all have the same width, the set of points forms a **regular partition** of the interval $[a,b]$.

^2971b4

>[!def] Definition Riemann Integral ([[../../../PDFs/zotero-182.pdf#page=25|Source]])
> Let $f(x)$ be defined on a closed interval $[a,b]$ and let $P$ be a [[#^2971b4|regular partition]] of $[a,b]$. Let $\Delta x$ be the width of each subinterval $[x_{i-1}, x_{i}]$ and for each $i$, let $x_{i}^*$ be any point in $[x_{i-1},x_{i}]$. A **Riemann sum** is defined for $f(x)$ as 
> $$\sum_{i=1}^n f(x_{i}^*)\Delta x$$

>[!def] Definition Definite Integral ([[../../../PDFs/zotero-182.pdf#page=35|Source]])
>If $f(x)$ is a function defined on an interval $[a,b]$, the **definite integral** of $f$ from $a$ to $b$ is given by
>$$\int _{a}^b f(x)\, dx = \lim_{ n \to \infty } \sum_{i=1}^n f(x_{i}^*)\Delta x$$
>provided the limit exists. If this limit exists, the function $f(x)$ is said to be integrable on $[a,b]$, or is an **integrable function**.

>[!theorem] Theorem Absolute Value Integral
>Let $f$ be continuous over the interval $[a,b] \subset \mathbb{R}$, then we can state
>$$ \left\lvert  \int_{a}^b f(x) \, dx   \right\rvert \leq \int _{a}^b \lvert f(x) \rvert  \, dx $$
>>[!proof]-
>>By the properties of the absolute value, we have
>>$$\begin{align}
>> -\lvert f(x) \rvert \leq f(x)\leq \lvert f(x) \rvert 
>>\end{align}$$
>>Integrating both sides
>>$$\begin{align}
>> -\int _{a}^b \, dx \lvert f(x) \rvert \leq \int _{a}^bf(x)\leq \int _{a}^b\lvert f(x) \rvert 
>>\end{align}$$
>>Using the following relation, we yield the desired statement
>>$$\begin{alignat}{2}
>> \int _{a}^bf(x)&\leq \int _{a}^b\lvert f(x) \rvert \qquad&&\Big\vert \;\;\lvert \,. \rvert \\
>> \left\lvert\int _{a}^bf(x)\right\rvert&\leq \int _{a}^b\lvert f(x) \rvert \tag*{$\square$} \\
>>\end{alignat}$$

^a5bf98

>[!theorem] Comparison Theorem  ([[../../../PDFs/zotero-182.pdf#page=46|Source]])
>1. If $f(x)\geq 0$ for $a \leq x \leq b$, then
>$$\int _{a}^b f(x)\, dx \geq 0$$
>2. If $f(x) \geq g(x)$ for $a \leq x \leq b$, then
>$$ \int _{a}^b f(x) \, dx \geq \int _{a}^b g(x) \, dx $$
>3. If $m$ and $M$ are constants such that $m \leq f(x) \leq M$ for $a \leq x \leq b$, then
>$$\begin{align}
> m(b-a) &\leq \int _{a}^bb f(x) \, dx \leq M(b-a) 
>\end{align}$$

^883fc9

>[!theorem] The Mean Value Theorem for Integrals ([[../../../PDFs/zotero-182.pdf#page=55|Source]])
> If $f(x)$ is continuous over an interval $[a,b]$, then there is at least one point $c \in [a,b]$ such that
> $$f(c) = \frac{1}{b-a}\int _{a}^b f(x) \, dx $$
> This formula can also be stated as
> $$\int _{a}^b f(x) \, dx = f(c)(b-a) $$
>>[!remark]
>> The main idea is that a continuous function $f$ over a closed interval $[a,b]$ takes its average value $f(x)$ at some point $c$.  This means, that we take the length of the interval, i.e. $b-a$, and calculate with this the average of the interval over $f(x)$, i.e. $\frac{1}{b-a}\int _{a}^b f(x) \, dx$. The theorem states, we can find a point $c$ within the interval $[a,b]$ which attains this average.
>
>>[!proof]-
>>Since $f(x)$ is continuous on the closed interval $[a,b]$ it will attain its minimum and maximum values on that interval $[a,b]$
>>$$\begin{align}
>>\underset{x \in [a,b]}{\text{min}}f(x) &= m \\
>>\underset{x \in [a,b]}{\text{max}}f(x) &= M
>>\end{align}$$
>>Therefore, we can state the relation
>>$$m \leq f(x) \leq M$$
>>by the [[#^883fc9| comparison theorem (3)]] we have
>>$$\begin{alignat}{3}
>> m(b-a) &\leq \int _{a}^b f(x) \, dx &\leq M(b-a) \qquad&&\Big\vert :(b-a) \\
>> m &\leq \frac{1}{b-a}\int _{a}^b f(x) \, dx &\leq M \qquad
>>\end{alignat}$$
>>Note that the expression $\frac{1}{b-a}\int _{a}^b f(x)$ is bounded by $m$ and $M$. Since $f$ is continuous over $[a,b]$ we know there exists a number $c \in [a,b]$ such that we have
>>$$\begin{align}
>>f(c) = \frac{1}{b-a}\int _{a}^b f(x) \, dx  \tag*{$\square$}
>>\end{align}$$ 

^d7a2e0

>[!Theorem] Fundamental Theorem of Calculus Part 1 ([[../../../PDFs/zotero-182.pdf#page=90|Source]])
>If $f(x)$ is continuous over an interval $[a,b]$, and the function $F(x)$ is defined by
>$$F(x)=\int _{a}^x f(t) \, dt $$
>then $F'(x)= f(x)$ over $[a,b]$.
>>[!proof]-
>>$$\begin{align}
>> F'(x) &= \lim_{ h \to 0 } \frac{F(x+h)-F(x)}{h} \tag{Definition Derivative}\\
>>       &= \lim_{ h \to 0 } \frac{1}{h} \int _{a}^{x+h}f(t) \, dt - \int _{a}^x f(t) \, dt  \tag{Definition Theorem} \\
>>       &= \lim_{ h \to 0 } \frac{1}{h} \int _{a}^{x+h}f(t) \, dt + \int _{x}^a f(t) \, dt  \tag{Integral Property} \\
>>       &= \lim_{ h \to 0 } \frac{1}{h} \int _{x}^{x+h}f(t) \, dt   \tag{Integral Property} \\
>>\end{align}$$
>>Note, the last equation is the [[#^d7a2e0| mean value]] over the interval $[x, x+h]$, therefore we can state by the [[#^d7a2e0| mean value theorem for integrals]] 
>>$$\begin{align}
>> \frac{1}{h} \int _{x}^{x+h}f(t) \, dt = f(c)
>>\end{align}$$
>>Note we have
>>$$\begin{align}
>> \lim_{ h \to 0 }f(c)=\lim_{ c \to x } f(c) = f(x) 
>>\end{align}$$
>>Therefore, putting everything together, we have
>>$$\begin{align}
>> F'(x) &= \lim_{ h \to 0 } \frac{1}{h}\int _{x}^{x+h} f(x) \, dx \\
>> &= \lim_{ h \to 0 } f(c) \\
>> &= f(x) \tag*{$\square$}
>>\end{align}$$

^8f29c7

>[!Theorem] Fundamental Theorem of Calculus Part 2 ([[../../../PDFs/zotero-182.pdf#page=90|Source]])
>If $f$ is continuous over the interval $[a,b]$ and $F(x)$ is any antiderivative of $f(x)$, then 
>$$\int _{a}^b f(x) \, dx = F(b)- F(a) $$

^f18d9f


>[!Theorem] Theorem Substitution Rule for Indefinite Integrals ([[../../../PDFs/briggs2019.pdf#page=414|Source 1]], [[../../../PDFs/zotero-182.pdf#page=90|Source 2]])
> Let $u=g(x)$, where $g$ is differentiable on an interval, and let $f$ be continuous on the corresponding range of $g$. On that interval
> $$\begin{align}
>\int  \underbrace{ f\Big(g(x)\Big) }_{ f(u) }\underbrace{ g'(x) }_{ du } \, dx &= \int f(u) \, du  \\
> &= F(u) + c  \\
> &= F\Big(g(x)\Big) + c
>\end{align}$$
>>[!note]-
>>The substitution rule reverses the chain rule of derivation
>
>>[!proof]-
>>Let $f,g,u$ and $F$ be as specified in the theorem. Then 
>>$$\begin{align}
>> \frac{d}{dx}F(g(x)) &= F'(g(x))g'(x) \tag{Chain Rule} \\
>> &= f(g(x))g'(x)
>>\end{align}$$
>>Integrating both sides with respect to $x$, we have
>>$$\begin{align}
>> F(g(x)) + c&= \int f(g(x))g'(x) \, dx 
>>\end{align}$$
>>Substituting $u= g(x)$ and $du = g'(x) dx$ we yield
>>$$\begin{align}
>> \int f(g(x))g'(x) \, dx &= \int f(u) \, du \\ 
>> &= F(u) + c  \\
>> &= F(g(x))+ c \tag*{$\square$} 
>>\end{align}$$
>
>>[!example]- Example Solve $\int  6x (3x^2 +4 )^4 \, dx$
>>Solving with the substitution rule we choose $u=3x^2 + 4$. We have
>>$$ \int u^4  \, du = \frac{u^5}{5} + c$$
>>Substituting back yields
>>$$ \frac{(3x^2 + 4)^5}{5}+c$$
>
>>[!example]- Example Solve $\int  z \sqrt{ z^2 -5 } \, dz$
>>We rewrite the integral as
>>$$\int  z \left(z^2 - 5\right)^{1/2} \, dz \tag{1}$$
>>We identify
>>$$\begin{alignat}{2}
>> u &= z^2 - 5 \\
>> &= g(z)\\
>> f(u) &= u^{1/2} \\
>> &= (z^2 - 5)^{1/2} \\
>> \frac{du}{dz} &= 2z \qquad&&\Big\vert \cdot dz\\
>> du &= 2z \,dz \tag{2} 
>>\end{alignat}$$
>>Note our results currently substitute the following terms in $(1)$
>>$$\int \underbrace{ (z^2-5)^{1/2} }_{ =f(u) } \, \underbrace{ z\,dz }_{ \text{remaining} } $$
>>We rearrange $(2)$ to find a proper term to substitute
>>$$\begin{alignat}{2}
>> du &= 2z \,dz \qquad&&\Big\vert \cdot \frac{1}{2}\\
>> \frac{1}{2}du &= z dz
>>\end{alignat}$$
>>Now can successfully substitute with $u$ and $f(u)=u^{1/2}$, i.e.
>>$$\begin{align}
>> \int \underbrace{ (z^2-5)^{1/2} }_{ =f(u) } \, \underbrace{ z\,dz }_{ \frac{1}{2} \, du }  &= \int  \frac{1}{2}u^{1/2} \, du  \\
>> &= \frac{1}{2} \int  u^{1/2} \, du  \\
>> &= \frac{1}{2} \frac{2}{3}u^{3/2} + c\\
>> &= \frac{1}{3}u^{3/2} + c\\
>>\end{align}$$
>>Substituting back gives
>>$$\int  z \left(z^2 - 5\right)^{1/2} \, dz =  \frac{1}{3}(z^2-5)^{3/2}+c$$
>
>^thmSubstitutionRuleIndef

>[!Theorem] Theorem Substitution Rule for Definite Integrals ([[../../../PDFs/briggs2019.pdf#page=418|Source]])
> Let $u = g(x)$, where $g'$ is continuous on $[a,b]$ and let $f$ be continuous on the range of $g$, and let $F(x)$ be an antiderivative of $f(x)$. Then,
> $$ \int_a^b f\Big(g(x)\Big)g'(x) \,dx = \int_{g(a)}^{g(b)}f(u) \, du$$
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
>^thmSubstitutionRuleDef


>[!Theorem] Theorem Integration by Parts ([[../../../PDFs/briggs2019.pdf#page=550|Source 1]], [[../../../PDFs/zotero-182.pdf#page=270|Source 2]])
> Let $u = f(x)$ and $v=g(x)$ be functions with continuous derivatives. The integration by parts formula for the given two functions can be formulated as
> $$ \int u\, dv \, = uv - \int v \,du  $$
>>[!proof]-
>>Let $h(x) = f(x)g(x)$. Using the product rule we have
>>$$ h'(x) = f'(x)g(x)+ g'(x)f(x)$$
>>Integrating both sides gives
>>$$ \int h'(x) \, dx = \int  g(x) f'(x) \, dx + \int  f(x) g'(x)\, dx $$ 
>>Now we solve for $\int f(x)g'(x) dx$
>>$$ \int f(x)g'(x)  \, dx = f(x)g(x) - \int g(x)f'(x) \, dx $$ 
>>Doing the substitution 
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
>>[!example]- Example $\int  x \sin (x) \, dx$  ([[../../../PDFs/zotero-182.pdf#page=270|Source]])
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
>>[!example]- Example $\int \frac{\ln x}{x^3} \,dx$ ([[../../../PDFs/zotero-182.pdf#page=272|Source]])
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