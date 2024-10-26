>[!lemma] Proposition ([[../../../../PDFs/judson2022.pdf#page=204|Source]])
>Let $R$ be a ring with $a,b \in R$, then
>1. $a0=0a=0$
>2. $a(-b)=(-a)b=-ab$
>3. $(-a)(-b)=ab$
>
>>[!proof]-
>>1. $\,$ $$a0=a(0+0)=a0 + \underbrace{ a0 }_{ =0 }$$
>>Hence $a0=0$. The direction for $0a$ works similarly.
>>
>>2. We want to show that $a(-b)+ab = 0$  $$ab + a(-b)=a(b-b)=a 0=0$$
>>3. Follows from (2)
>>$$(-a)(-b)=-(a(-b))=-(-ab)= ab \tag*{$\square$}$$

>[!def] Definition Subring ([[../../../../PDFs/judson2022.pdf#page=205|Source]])
>Let $R$ be a ring. Then $S$ is a **<span style="color:#38ffa9">subring</span>** if
>1. $S \subset R$
>2. $S$ is a [[1 - Algebraic Structures#^2c4055|ring]] under the inherited operations from $R$

>[!lemma] Proposition
> Let $R$ be a ring and $S$ a subset of $R$. Then $S$ is a **<span style="color:#3884ff">subring</span>** of $R$ if and only if the following conditions are satisfied:
> 1. $S \neq \emptyset$
> 2. $rs \in S$ for all $r,s \in S$
> 3. $r-s \in S$ for all $r,s \in S$


## Integral Domains

>[!def] Definition Zero Divisor ([[../../../../PDFs/judson2022.pdf#page=205|Source]])
>Let $R$ be a [[1 - Algebraic Structures#^4a5286|commutative ring]] and $r \in R$ with $r \neq 0$. The element $r$ is called **<span style="color:#38ffa9">zero divisor</span>** if there is some $s \in R$ with $s \neq 0$, such that
>$$rs =0$$

>[!remark] Recall
> A ring is an [[1 - Algebraic Structures#^f48d09|integral domain]] if it has no **<span style="color:#e9ffad">zero divisors</span>**.