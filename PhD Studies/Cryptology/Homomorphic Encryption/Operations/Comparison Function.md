>[!def] Definition Comparison Function ([[../../../../PDFs/Iliashenko2021.pdf|Source]])
> Let $S$ be a totally ordered set with a binary relation $<$. For any $x,y \in \mathcal{S}$, we can define the **<span style="color:#38ffa9">less-than</span>** and the **<span style="color:#38ffa9">equality function</span>** as follows
> $$\begin{align}
> \text{LT}_{\mathcal{S}}(x,y)&=\begin{cases}
> 1, &\text{ if } x<y \\
> 0, &\text{ if } x\geq y \\
>\end{cases}  \\
>\text{EQ}_{\mathcal{S}}(x,y)&= \begin{cases}
>  1, &\text{ if } x=y \\
> 0, & \text{ if } x \neq y  
>\end{cases}
>\end{align}$$



>[!def] Definition Principal Character ([[../../../../PDFs/Iliashenko2021.pdf|Source]])
>Let $\mathbb{F}_{p^{d}}$ denote the extension field  $\mathbb{F}_{p^d}/\mathbb{F}_{p}$ where $p$ denotes a prime number and $d \geq 1$. Then the mapping
>$$\begin{align}
> &\chi: x \mapsto x^{{p}^d-1} \\
> &\chi:\mathbb{F}_{p^d} \to \{ 0,1 \}
>\end{align}$$
>is called **<span style="color:#38ffa9">principal character</span>** function. The principal character function can be calculated using Euclid's theorem as
>$$\chi(x)=\begin{cases}
> 0 &\text{ if } x=0 \\
> 1 & \text{ else }
>\end{cases}$$

>[!lemma] Lemma Lagrange Interpolation
>Every function $$f: \mathbb{F}_{p^d}^l \to \mathbb{F}_{p^d}$$
>with $l\geq 1$ is a polynomial function represented by a unique polynomial $P_{f}(X_{1},\dots X_{l})$ of degree at most $p^d-1$ in each variable. In particular
>$$P_{f}(X_{1},\dots,X_{l})= \sum_{\mathbf{a} \in \mathbb{F}^l_{p^d}} f(\mathbf{a}) \prod_{i=1}^l(1-\chi(X_{i}-a_{i})) \;\;(\text{mod } p)$$
>where $a_{i}$ is the $i$-th coordinate of vector $\mathbf{a}$.
>
>>[!example]
>> Let $$\begin{align}
>> p&=2 \\
>> d&=1 \\
>> l&=1
>>\end{align}$$
>>where the resulting **<span style="color:#f7b8ff">field</span>** is
>>$$\mathbb{F}_{2}=\{ 0,1 \}$$
>>and the **<span style="color:#f7b8ff">field extension</span>**
>>$$\mathbb{F}_{2^1}^2 = \mathbb{F}_{2}^2$$
>>We define the **<span style="color:#f7b8ff">function</span>**
>>$$f: \mathbb{F}_{2}^2 \to \mathbb{F}_{2}$$
>>with $x_{1},x_{2} \in \mathbb{F}_{2}$
>>$$f(x_{1},x_{2})=\begin{cases}
>> 0 & \text{ if } x_{1}=0, &x_{2}=0 \\
>> 1 & \text{ if } x_{1}=1, &x_{2}=0 \\
>> 1 & \text{ if } x_{1}=0, &x_{2}=1 \\
>> 0 & \text{ if } x_{1}=1, &x_{2}=1 \\
>>\end{cases}$$
>>which is the XOR function, i.e.
>>$$f(x_{1},x_{2})= (x_{1} + x_{2}) \text{ mod } 2$$
>>
>>According to the lemma we can represent the function as a polynomial, i.e.
>>$$P_{f}(X_{1},X_{2})=\sum_{\mathbf{a} \in \mathbb{F}_{2}^2} f(\mathbf{a}) \prod_{i=1}^2 (1-\chi(X_{i}-a_{i}))$$
>>Denote the summand 
>>$$S(\mathbf{a})=f(\mathbf{a}) \prod_{i=1}^2 (1-\chi(X_{i}-a_{i})) \;\;(\text{mod } 2)$$
>>for a particular $\mathbf{a}\in \mathbb{F}_{2}^2$
>>---
>>1. $\mathbf{a}=(0,0)$$$\begin{align}
>>S\Big((0,0)\Big) &= \underbrace{ f\Big(1,1\Big) }_{ =0 } \prod_{i=1}^2 (1-\chi(X_{i}-a_{i})) &&\;\;(\text{mod } 2)\\
>> &=0 &&\;\;(\text{mod } 2)
>>\end{align}$$
>>2. $\mathbf{a}=(0,1)$
>>$$\begin{align}
>> S\Big((0,1)\Big) &\equiv \underbrace{ f\Big(0,1\Big) }_{ =1 } \prod_{i=1}^2 (1-\chi(X_{i}-a_{i})) &&\;\;(\text{mod } 2)\\
>> &\equiv \underbrace{ \Big(1-\chi\big(X_{1}-0)\big) }_{ (1) }\underbrace{ \big(1-\chi(X_{2}-1\big)\Big) }_{ (2) } &&\;\;(\text{mod } 2)\\
>>\end{align}$$
>><u>Case $(1)$ </u>
>>$$\begin{align}
>>X_{1}=0 &\implies 1-\chi(0-0)\equiv 1 &&\;\;(\text{mod } 2) \\
>>X_{1}\neq 0 &\implies 1-\chi(X_{1}-0)\equiv 0 &&\;\;(\text{mod } 2) 
>>\end{align}$$
>>in dependence of $X_{1}$ $(1)$ can be represented as
>>$$(1) \widehat{=} 1-X_{1}$$
>> <u>Case $(2)$</u>
>> $$\begin{align}
>> X_{2}=1 &\implies 1-\chi(1-1)\equiv 1 &&\;\;(\text{mod } 2)\\
>> X_{2}\neq 1 &\implies 1-\chi(X_{2}-1)\equiv 0 &&\;\;(\text{mod } 2)  \\
>> &\phantom{\implies \;\;\;}1 - (X_{2}-1) \equiv 0 &&\;\;(\text{mod } 2)\\
>> &\phantom{\implies \;\;\;\;\;\;\;\;\;\;\;\;}2 - X_{2} \equiv 0 &&\;\;(\text{mod } 2)\\
>> &\phantom{\implies \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\,\;} X_{2} \equiv 0 &&\;\;(\text{mod } 2)
>>\end{align}$$
>>again in dependence of $X_{2}$, $(2)$ can be represented as
>>$$(2)\widehat{=}X_{2}$$
>>We finally receive
>>$$S\Big((0,1)\Big)=(1-X_{1})X_{2}$$
>>3. $\mathbf{a}=(1,0)$
>>By the symmetry behavior of the procedure we get
>>$$S\Big((0,1)\Big)=X_{1}(1-X_{2})$$
>>4. $\mathbf{a}=(1,1)$$$\begin{align}
>>S\Big((0,0)\Big) &= \underbrace{ f\Big(1,1\Big) }_{ =0 } \prod_{i=1}^2 (1-\chi(X_{i}-a_{i})) &&\;\;(\text{mod } 2)\\
>> &=0 &&\;\;(\text{mod } 2)
>> \end{align}$$
>>---
>>The final polynomial is given as
>>$$\begin{align}
>> P_{f}(X_{1},X_{2})&=\sum_{\mathbf{a} \in \mathbb{F}_{2}^2} f(\mathbf{a}) \prod_{i=1}^2 (1-\chi(X_{i}-a_{i})) &&\;\;(\text{mod } 2)\\
>> &\equiv \underbrace{ 0 }_{ \mathbf{a}=(0,0) } + \underbrace{ (1-X_{1})X_{2} }_{ \mathbf{a}=(0,1) }+\underbrace{ X_{1}(1-X_{2}) }_{ \mathbf{a}=(1,0) }+\underbrace{ 0 }_{ \mathbf{a}=(1,1) } &&\;\;(\text{mod } 2) \\
>> &\equiv (1-X_{1})X_{2} + X_{1}(1-X_{2}) &&\;\;(\text{mod } 2)
>>\end{align}$$

<!-- -->