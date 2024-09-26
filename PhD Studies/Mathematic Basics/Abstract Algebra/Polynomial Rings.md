>[!attention] Attention Throughout this document $R$ is an [[Algebraic Structures#^4a5286|commutative ring]] with [[Algebraic Structures#^0b2e62|identity element]].

>[!def] Definition Polynomial over $R$ ([[../../../PDFs/judson2022.pdf#page=221|Source]])
>Let $R$ be an [[Algebraic Structures#^4a5286|commutative ring]] with [[Algebraic Structures#^0b2e62|identity element]]. The function 
>$$\begin{align}
> f(x) &= \sum_{i=0}^ {n} a_{i}x^{i} \\
> &= a_{0} + a_{1}x + a_{2}x^2 + \dots + a_{n}x^n
>\end{align}$$
>is called a **polynomial over** $R$, where $a_{i} \in R$, $a_{n}\neq 0$ and $x$ being indeterminate. We denote the set of all polynomials with respect to the ring $R$ as $R[x]$
>>[!remark] Remark on Terminology
>>1. $x$ being **<span style="color:#e9ffad">indeterminate</span>** means, that $x$ does not need to be specified. It is just a formal symbol for describing the polynomial, but not mappings will be performed, hence domain and codomain are not of interest
>>
>>2.  $a_{0},a_{1},\dots,a_{n}$ are called the **<span style="color:#e9ffad">coefficients of $f$</span>**
>>3. $a_{n}$ is called the **<span style="color:#e9ffad">leading coefficient</span>**
>>4. if $a_{n}=1$ the polynomial is called **<span style="color:#e9ffad">monic</span>**
>>5. if $n$ is the largest non-negative number with $a_{n}\neq 0$, we say $n$ is **<span style="color:#e9ffad"> the degree of $f$</span>** and write **<span style="color:#e9ffad">$\text{deg } f(x)=n$</span>**
>>6. if no such $n$ exists then **<span style="color:#e9ffad"> $f=0$ </span>**is the **<span style="color:#e9ffad">zero-polynomial</span>** with the degree <span style="color:#e9ffad">$\text{deg } f(x)=-\infty$</span> 

>[!def] Definition Equivalency of Polynomials ([[../../../PDFs/judson2022.pdf#page=222|Source]])
>Let $f,g \in R[x]$. We say **~={green} $f$ is equivalent to $g$=~** if their coefficients are equal, i.e. for
>$$\begin{align}
>f(x) &= \sum_{i=0}^{n} a_{i}x^{i} \\
>g(x) &= \sum_{i=0}^{n} b_{i}x^{i}
>\end{align}$$
>we get
>$$f(x) = g(x):\iff a_{i}=b_{i} \; \text{ with }0 \leq i \leq n $$

>[!def] Definition Addition of Polynomials ([[../../../PDFs/judson2022.pdf#page=222|Source]])
>Let $f,g \in R[x]$. We define the **~={green}addition of two polynomials=~** for 
>$$\begin{align}
>f(x) &= \sum_{i=0}^{n} a_{i}x^{i} \\
>g(x) &= \sum_{i=0}^{m} b_{i}x^{i}
>\end{align}$$
>with $c_{i}=a_{i}+b_{i}$ for $0 \leq i \leq n$ as
>$$f(x)+g(x):=\sum_{i=0}^{\text{max}\{n,m \}} c_{i}x^i$$

^b39226

>[!def] Definition Multiplication of Polynomials ([[../../../PDFs/judson2022.pdf#page=222|Source]])
>Let $f(x),g(x) \in R[x]$. We define the **~={green}multiplication of two polynomials=~** for 
>$$\begin{align}
>f(x) &= \sum_{i=0}^{n} a_{i}x^{i} \\
>g(x) &= \sum_{i=0}^{m} b_{i}x^{i}
>\end{align}$$
>with $$\begin{align}
> c_{i}&=\sum_{k=0}^i a_{k}b_{i-k} \\
> &= a_{0}b_{i} + a_{1}b_{i-1} + \dots + a_{i-1}b_{1} + a_{i}b_{0}
>\end{align}$$ for $0 \leq i \leq n+m$ as
>$$f(x)\cdot g(x):=\sum_{i=0}^{n+m} c_{i}x^{i}$$
>>[!example]-
>>Let $$\begin{align}
>> p(x)&= 3+0x+0x^2+2x^3+0x^4 \\
>> q(x)&= 2+0x-1x^2+0x^3+4x^4
>>\end{align}$$
>>We get
>>$$\begin{align}
>> p(x)+q(x)&= 5-x^2+2x^3+4x^4 \\
>> p(x)\cdot q(x)&= 6-3x^2 +4x^3+12x^4-2x^5+8x^7
>>\end{align}$$

^2f1176

>[!theorem] Theorem Polynomials over $R$ is a Commutative Ring ([[../../../PDFs/judson2022.pdf#page=223|Source]])
>Let $R$ be an [[Algebraic Structures#^4a5286|commutative ring]] with [[Algebraic Structures#^0b2e62|identity element]], then **~={green}$R[x]$ is a commutative ring with identity=~**
>>[!proof] Proof can be seen ([[../../../PDFs/judson2022.pdf#page=215|here]]), it is just some algebraic operations.

>[!lemma] Proposition Degree of Integral Domain Products ([[../../../PDFs/judson2022.pdf#page=224|Source]])
>Let $p(x), q(x) \in R[x]$ with $R$ being an [[Algebraic Structures#^f48d09|integral domain]], then
>$$\text{deg }p(x) + \text{deg }q(x) = \text{deg }\Big(p(x)q(x)\Big)$$
>Furthermore, $$R[x]$$ is an [[Algebraic Structures#^f48d09|integral domain]].
>>[!proof]-
>>We start with the degree claim. Let $p(x),q(x) \in R[x]$ be non-zero with
>>$$\begin{align}
>> p(x) &= \sum_{i=0}^{m}a_{i}x^i \text{ with } \text{deg }p(x)=m\\
>> q(x) &= \sum_{i=0}^{n}b_{i}x_{i} \text{ with deg } q(x)=n
>>\end{align}$$
>>and $a^n \neq 0, b^m \neq 0$. The leading term of their product is
>>$$p(x)q(x) \underset{\text{term}}{\overset{\text{leading}}{\implies}} a_{m}b_{n}x^{m+n}$$
>>which cannot be zero by the definition of the [[Algebraic Structures#^f48d09|integral domain]], hence
>>$$\text{deg }\Big(p(x)q(x)\Big) = n\cdot m = \text{deg }p(x) \cdot \text{deg }q(x)\tag*{$\checkmark$}$$
>>---
>>Now we show, that $R[x]$ is an [[Algebraic Structures#^f48d09|integral domain]]. Therefore, it must hold $$p(x)\cdot q(x) = 0 \iff p(x) = 0 \lor q(x)=0$$
>>Since both $p(x),q(x) \neq 0$ their product can't become $0$, hence $R[x]$ is an [[Algebraic Structures#^f48d09|integral domain]]$$\tag*{$\checkmark$}$$
>>---
>>$$\tag*{$\square$}$$

^b25d21

>[!theorem] Theorem Ring [[../../Cryptology/Homomorphic Encryption/Basics on Homomorphic Encryption#^c817ef|Homomorphism]] ([[../../../PDFs/judson2022.pdf#page=224|Source]])
>Let $R$ be a [[Algebraic Structures#^4a5286|commutative ring]] with identity and $\alpha \in \mathbb{R}$, then we have a **~={green}ring homomorphism=~** $\phi_{\alpha}: R[x]\to R$ defined by $$\phi_{\alpha}\Big(p(x)\Big)= p(\alpha)= a_{n}\alpha^n + \dots + a_{1}\alpha + a_{0}$$ where $p(x)=a_{n}x^n+\dots+a_{1}x+a_{0}$
>>[!proof]-
>> Let $p(x),q(x) \in R[x]$ be non-zero with
>>$$\begin{align}
>> p(x) &= \sum_{i=0}^{m}a_{i}x^i \\
>> q(x) &= \sum_{i=0}^{n}b_{i}x_{i} 
>>\end{align}$$
>>
>>---
>>
>>We first show that the [[Algebraic Structures#^c3d051|ring homomorphism]] holds regarding [[#^b39226|addition]]
>>$$\begin{align}
>> \phi_{\alpha}\Big(p(x)+q(x)\Big) &= \sum_{i=0}^{\max\set{m,n}} (a_{i}+b_{i})\alpha^i \\
>> &= \sum_{i=0}^{\max\set{m,n}} a_{i}\alpha^i+b_{i}\alpha^i \\
>> &= \sum_{i=0}^{m}a_{i}\alpha^i + \sum_{i=0}^{n}b_{i}\alpha^i \\
>> &= \phi_{\alpha}\Big(p(x)\Big) + \phi_{\alpha}\Big(q(x)\Big) \tag*{$\checkmark$}
>>\end{align}$$
>>
>>---
>>We now show that the [[Algebraic Structures#^c3d051|ring homomorphism]] holds regarding [[#^2f1176|multiplication]]
>>$$\begin{align}
>> \phi_{\alpha}\Big(p(x)\Big)\phi_{\alpha}\Big(q(x)\Big)&= p(\alpha)q(\alpha) \\
>> &= \left( \sum_{i=0}^m a_{i}\alpha^i \right) \left( \sum_{i=0}^n b_{i}\alpha^i \right)  \\
>> &= \sum_{i=0}^{m+n}\left( \sum_{k=0}^{i}a_{k}b_{i-k} \right)\alpha^i
>> &= \phi_{\alpha}\Big(p(x)q(x)\Big) \tag*{$\checkmark$}
>>\end{align}$$
>>$$\tag*{$\square$}$$

## The Division Algorithm

>[!theorem] Theorem Division Algorithm ([[../../../PDFs/judson2022.pdf#page=224|Source]])
>Let $p(x), q(x) \in F[x]$ with $F$ being a [[Algebraic Structures#^a17f1c|field]] and $g(x)\neq 0$. Then**~={green} there exist unique polynomials $q(x),r(x) \in F[x]$=~** such that
>$$f(x)=g(x)q(x)+r(x)$$
>where $\text{deg }r(x)<\text{deg }g(x)$ or $\text{deg }r(x)=0$.
>>[!remark] Remark on Terminology
>> We call
>> - $g(x)$ the **~={yellow}quotient of $f(x)$=~**
>> - $r(x)$ the **~={yellow}residue with respect to the quotient $g(x)$=~**
>
>>[!proof]-
>><u>Proof of Existence of $g(x)$ and $r(x)$</u>:
>>1. First Case:  Consider $f(x)=0$, then
>>$$0 = \underbrace{ 0 }_{ =q(x) } \cdot g(x) + \underbrace{ 0 }_{ =r(x) }$$
>>
>>For the next two cases consider
>>- $f(x)\neq 0$
>>- $\text{deg }f(x)=n$ 
>>- $\text{deg }g(x)=m$ 
>>2. Second Case: $m>n$ $\implies$ $q(x)=0$ and $r(x)=f(x)$ solves, there can't be any other solution in this case.
>> 3. Third Case: For $m \leq n$ we will use induction on the degree of $f$. <br>
>> <u>Induction Start:</u> $\text{deg }f(x)=0=n$
>> Here it must follow $\text{deg } g(x)=0$. Therefore, we get
>> $$\begin{align}
>> f(x)&= a \tag*{$a \in F$} \\
>> g(x)&=b \tag*{$b \in F$}
>>\end{align}$$
>>Then by our hypothesis, the following must hold true
>>$$a = bq(x)+r(x)$$
>>Since $F$ is a [[Algebraic Structures#^a17f1c|Field]] the inverse with respect to multiplication exists. We choose $r(x)=0$ and find
>>$$a = b(b^{-1}a) + 0 \tag*{$\checkmark$}$$
>><u>Inductionstep:</u>
>>We now assume, that the hypothesis is true for any $f$ with $\text{deg }f(x)<n$. We denote 
>>$$\begin{align}
>> f(x) &= a_{n}x^n+ \dots+a_{1}x+a_{0} \\
>> g(x)&= b_{m}x^m+\dots+b_{1}+b_{0} 
>>\end{align}$$
>>with $a_{n}, b_{m} \neq 0$. We prepare $g(x)$
>>$$\begin{align}
>> g(x)&=b_{m}x^m+\dots+b_{1}+b_{0}  \qquad&&\Big\vert \cdot a_{n}b_{m}^{-1}x^{n-m} \\
>> a_{n}b_{m}^{-1}x^{n-m}g(x)    &=(a_{n}b_{m}^{-1}x^{n-m})(b_{m}x^m+\dots+b_{1}+b_{0})   \\
>> &= a_{n}x^n+a_{n}b_{m}^{-1}b_{m-1}x^{m-1}+\dots+a_{n}b_{m}^{-1}b_{0}x^{n-m}
>>\end{align}$$
>>We now denote
>>$$f'(x)=f(x)-a_{n}b_{m}^{-1}x^{n-m}g(x)$$
>>which will be a polynomial with $0 \leq \text{deg }f'(x)\leq n-1$. Thus, there exists polynomials $q_{1}(x)$ and $r(x)$ such that
>>$$\begin{align}
>> f'(x)=q_{1}(x)g(x)+r(x)
>>\end{align}$$
>>with either $r(x)=0$ or $\text{deg }r(x)<\text{deg }g(x)$, therefore we can make the same conclusion for
>>$$f(x)=a_{n}b_{m}^{-1}x^{n-m}g(x) + f'(x)$$
>>which concludes the induction. $$\tag*{$\checkmark$}$$
>>>[!note]- Note, the remainders for $f(x)$ and $f'(x)$ are the same
>>>$$\begin{align}
>>> f'(x)&=f(x)-a_{n}b_{m}^{-1}x^{n-m}g(x) \\
>>> f(x) &= a_{n}b_{m}^{-1}x^{n-m}g(x) + f'(x)  \\
>>> f(x) &= a_{n}b_{m}^{-1}x^{n-m}g(x) + q_{1}(x)g(x)+r(x)  \tag{def of $f'(x)$}\\
>>> f(x) &= \Big(a_{n}b_{m}^{-1}x^{n-m} + q_{1}(x)\Big)g(x)+r(x)  \\
>>>\end{align}$$ 
>>---
>>
>><u> Proof of Uniqueness of $g(x)$ and $r(x)$:</u>
>>Suppose there exist $q'(x) \neq q(x)$ and $r'(x)\neq r(x)$ satisfying
>>$$f(x)=q'(x)g(x)+r'(x)$$ 
>>with either $r'(x)=0$ or $\text{deg }r'(x)<\text{deg }g(x)$, then the following must be true
>>$$q(x)g(x)+r(x) = f(x) = q'(x)g(x)+r'(x)$$
>>which can be transformed to
>>$$g(x)\Big(q(x)-q'(x)\Big) = r'(x)-r(x)$$
>>Unless $q(x)-q'(x)=0$ the degrees of the left-hand side and right-hand side can't be equal, because the degree of the left-hand side will always be greater than the one of the right-hand side. This is a contradiction to our assumption. Therefore, the only solution is 
>>$$\begin{align}
>> q(x)-q'(x)&=0 \implies q(x)=q'(x) \\
>> r(x)-r'(x)&=0 \implies r(x)=r'(x)
>>\end{align}$$
>>which shows that the elements must be unique. This establishes the theorem.
>>$$\tag*{$\square$}$$
>
>>[!remark] Remark on Long Division
>>This theorem formalizes the long division

^f8881d

>[!lemma] Corollary Polynomial Factorization over Roots ([[../../../PDFs/judson2022.pdf#page=226|Source]])
>Let $F$ be a [[Algebraic Structures#^a17f1c|field]]. An element $\alpha \in F$ is a **~={blue}zero=~** or **~={blue}root=~** of  $p(x)\in F[x]$ **if and only if** $(x-\alpha)$ is a factor of $p(x)\in F[x]$
>>[!proof]-
>>1. $\implies$:
>>Suppose $\alpha \in F$ with $p(\alpha)=0$. By the [[#^f8881d|division algorithm]], there exist polynomials $q(x),r(x) \in F[x]$ such that
>>$$p(x)=\underbrace{ (x-\alpha) }_{ =g(x) }q(x)+r(x)$$
>>Since $\text{deg }g(x)=1$ and $\text{deg }r(x)<\text{deg } g(x)$ it follows $\text{deg }r(x)=0$. Therefore, for some $a \in F$, we say
>>$$p(x)=(x-\alpha) q(x)+a$$
>>By our condition that $p(\alpha)=0$ we get
>>$$0 = p(\alpha)=0 q(\alpha)+a= a$$
>>Therefore, there can't be a remainder and $x-\alpha$ must be a factor of $p(x)$.
>>1. $\Longleftarrow$:
>>Suppose $x-\alpha$ is a factor of $p(x)$, then we get
>>$$p(x)=(x-\alpha)q(x)$$
>>When we map $x=\alpha$, we get
>>$$p(\alpha)= 0 q(x)= 0$$
>>$$\tag*{$\square$}$$

^4a5c83

>[!lemma] Corollary Relation of Number of Roots and Degree of a Polynomial ([[../../../PDFs/judson2022.pdf#page=226|Source]])
>Let $F$ be a [[Algebraic Structures#^a17f1c|field]]. A polynomial $p(x)\neq 0$ with $\text{deg }p(x)=n$ in $F[x]$ can have at most $n$ distinct zeros in $F$.
>>[!proof]- 
>>We will use induction on the $\text{deg } p(x)=n$.
>>
>><u>Induction Start:</u>
>>Suppose $\text{deg } p(x)=0$, then $p(x)=a$ and has no roots.
>>Suppose $\text{deg } p(x)=1$, then $p(x)=ax+b$ for some $a,b \in F$. If we suppose there are two roots $\alpha_{1},\alpha_{2} \in F$ we get
>>$$a\alpha_{1}+b=a \alpha_{2} +b \iff \alpha_{1}=\alpha_{2}$$
>>hence, $p(x)$ with degree $1$ has at most $1$ root. $$\tag*{$\checkmark$}$$
>><u>Induction Step:</u>
>>Assume $\text{deg }p(x)>1$. If $p(x)$ has no roots, the statement holds true. 
>>Assume $\alpha$ is a root of $p(x)$, then by the [[#^4a5c83|corollary of polynomial factorization over roots]] we can represent $p(x)$ as $$p(x)=(x-\alpha)q(x)$$
>>with $q(x)\in F[x]$. By the [[#^b25d21|proposition of integral domain products]], which can be used since a [[Algebraic Structures#^a17f1c|field]] is an extension of a [[Algebraic Structures#^f48d09|integral domain]], we know
>>$$\text{deg }q(x)= n-1$$
>>Now, assume $\beta \in F$ is another root of $p(x)$ different from $\alpha$. We map as follows
>>$$p(\beta)=(\beta-\alpha)q(\beta)=0$$
>>Since, $\alpha \neq \beta$ then it must follow that $q(\beta)=0$ because of the property of [[Algebraic Structures#^f48d09|integral domains]]. Therefore, $q(x)$ can have at most $n-1$ different roots different from $\alpha$. This results in $p(x)$ having at most $n$ roots, which establishes the corollary. $$\tag*{$\square$}$$

>[!lemma] Proposition Lemma of Bezout for Polynomials ([[../../../PDFs/judson2022.pdf#page=226|Source]])
> Let $F$ be a field and suppose that $d(x)$ is a greatest common divisor of two polynomials $p(x)$ and $q(x)$ in $F[x]$. Then there exist polynomials $r(x)$ and $s(x)$ such that
> $$d(x)=r(x)p(x)+s(x)q(x)$$
> Furthermore, the greatest common divisor of two polynomials is unique.
>>[!proof]