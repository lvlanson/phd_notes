>[!attention] Attention Throughout this document $R$ is an [[1 - Algebraic Structures#^4a5286|commutative ring]] with [[1 - Algebraic Structures#^0b2e62|identity element]].

## Basic Definitions and Properties of Polynomial Rings

>[!def] Definition Polynomial over $R$ ([[../../../../PDFs/judson2022.pdf#page=221|Source]])
>Let $R$ be an [[1 - Algebraic Structures#^4a5286|commutative ring]] with [[1 - Algebraic Structures#^0b2e62|identity element]]. The function 
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

^a2163f

>[!def] Definition Equivalency of Polynomials ([[../../../../PDFs/judson2022.pdf#page=222|Source]])
>Let $f,g \in R[x]$. We say  **<span style="color:#38ffa9">$f$ is equivalent to $g$</span>** if their coefficients are equal, i.e. for
>$$\begin{align}
>f(x) &= \sum_{i=0}^{n} a_{i}x^{i} \\
>g(x) &= \sum_{i=0}^{n} b_{i}x^{i}
>\end{align}$$
>we get
>$$f(x) = g(x):\iff a_{i}=b_{i} \; \text{ with }0 \leq i \leq n $$

>[!def] Definition Addition of Polynomials ([[../../../../PDFs/judson2022.pdf#page=222|Source]])
>Let $f,g \in R[x]$. We define the **<span style="color:#38ffa9">addition of two polynomials</span>** for 
>$$\begin{align}
>f(x) &= \sum_{i=0}^{n} a_{i}x^{i} \\
>g(x) &= \sum_{i=0}^{m} b_{i}x^{i}
>\end{align}$$
>with $c_{i}=a_{i}+b_{i}$ for $0 \leq i \leq n$ as
>$$f(x)+g(x):=\sum_{i=0}^{\text{max}\{n,m \}} c_{i}x^i$$

^b39226

>[!def] Definition Multiplication of Polynomials ([[../../../../PDFs/judson2022.pdf#page=222|Source]])
>Let $f(x),g(x) \in R[x]$. We define the **<span style="color:#38ffa9">multiplication of two polynomials</span>** for 
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

>[!theorem] Theorem Polynomials over $R$ is a Commutative Ring ([[../../../../PDFs/judson2022.pdf#page=223|Source]])
>Let $R$ be an [[1 - Algebraic Structures#^4a5286|commutative ring]] with [[1 - Algebraic Structures#^0b2e62|identity element]], then **~={green}$R[x]$ is a commutative ring with identity=~**
>>[!proof] Proof can be seen ([[../../../../PDFs/judson2022.pdf#page=215|here]]), it is just some algebraic operations.

>[!lemma] Proposition Degree of Integral Domain Products ([[../../../../PDFs/judson2022.pdf#page=224|Source]])
>Let $p(x), q(x) \in R[x]$ with $R$ being an [[1 - Algebraic Structures#^f48d09|integral domain]], then
>$$\text{deg }p(x) + \text{deg }q(x) = \text{deg }\Big(p(x)q(x)\Big)$$
>Furthermore, $$R[x]$$ is an [[1 - Algebraic Structures#^f48d09|integral domain]].
>>[!proof]-
>>We start with the degree claim. Let $p(x),q(x) \in R[x]$ be non-zero with
>>$$\begin{align}
>> p(x) &= \sum_{i=0}^{m}a_{i}x^i \text{ with } \text{deg }p(x)=m\\
>> q(x) &= \sum_{i=0}^{n}b_{i}x_{i} \text{ with deg } q(x)=n
>>\end{align}$$
>>and $a^n \neq 0, b^m \neq 0$. The leading term of their product is
>>$$p(x)q(x) \underset{\text{term}}{\overset{\text{leading}}{\implies}} a_{m}b_{n}x^{m+n}$$
>>which cannot be zero by the definition of the [[1 - Algebraic Structures#^f48d09|integral domain]], hence
>>$$\text{deg }\Big(p(x)q(x)\Big) = n\cdot m = \text{deg }p(x) \cdot \text{deg }q(x)\tag*{$\checkmark$}$$
>>---
>>Now we show, that $R[x]$ is an [[1 - Algebraic Structures#^f48d09|integral domain]]. Therefore, it must hold $$p(x)\cdot q(x) = 0 \iff p(x) = 0 \lor q(x)=0$$
>>Since both $p(x),q(x) \neq 0$ their product can't become $0$, hence $R[x]$ is an [[1 - Algebraic Structures#^f48d09|integral domain]]$$\tag*{$\checkmark$}$$
>>---
>>$$\tag*{$\square$}$$

^b25d21

>[!theorem] Theorem Ring [[../../../Cryptology/Homomorphic Encryption/Basics on Homomorphic Encryption#^c817ef|Homomorphism]] ([[../../../../PDFs/judson2022.pdf#page=224|Source]])
>Let $R$ be a [[1 - Algebraic Structures#^4a5286|commutative ring]] with identity and $\alpha \in \mathbb{R}$, then we have a **<span style="color:#38ffa9">ring homomorphism</span>** $\phi_{\alpha}: R[x]\to R$ defined by $$\phi_{\alpha}\Big(p(x)\Big)= p(\alpha)= a_{n}\alpha^n + \dots + a_{1}\alpha + a_{0}$$ where $p(x)=a_{n}x^n+\dots+a_{1}x+a_{0}$
>>[!proof]-
>> Let $p(x),q(x) \in R[x]$ be non-zero with
>>$$\begin{align}
>> p(x) &= \sum_{i=0}^{m}a_{i}x^i \\
>> q(x) &= \sum_{i=0}^{n}b_{i}x_{i} 
>>\end{align}$$
>>
>>---
>>
>>We first show that the [[1 - Algebraic Structures#^c3d051|ring homomorphism]] holds regarding [[#^b39226|addition]]
>>$$\begin{align}
>> \phi_{\alpha}\Big(p(x)+q(x)\Big) &= \sum_{i=0}^{\max\set{m,n}} (a_{i}+b_{i})\alpha^i \\
>> &= \sum_{i=0}^{\max\set{m,n}} a_{i}\alpha^i+b_{i}\alpha^i \\
>> &= \sum_{i=0}^{m}a_{i}\alpha^i + \sum_{i=0}^{n}b_{i}\alpha^i \\mathbf
>> &= \phi_{\alpha}\Big(p(x)\Big) + \phi_{\alpha}\Big(q(x)\Big) \tag*{$\checkmark$}
>>\end{align}$$
>>
>>---
>>We now show that the [[1 - Algebraic Structures#^c3d051|ring homomorphism]] holds regarding [[#^2f1176|multiplication]]
>>$$\begin{align}
>> \phi_{\alpha}\Big(p(x)\Big)\phi_{\alpha}\Big(q(x)\Big)&= p(\alpha)q(\alpha) \\
>> &= \left( \sum_{i=0}^m a_{i}\alpha^i \right) \left( \sum_{i=0}^n b_{i}\alpha^i \right)  \\
>> &= \sum_{i=0}^{m+n}\left( \sum_{k=0}^{i}a_{k}b_{i-k} \right)\alpha^i
>> &= \phi_{\alpha}\Big(p(x)q(x)\Big) \tag*{$\checkmark$}
>>\end{align}$$
>>$$\tag*{$\square$}$$
>

>[!def] Definition Evaluation Homomorphism ([[../../../../PDFs/judson2022.pdf#page=224|Source]])
>Let $R$ be a [[#^4a5286|commutative ring]] with identity and $\alpha \in R$. The map
>$$\phi_{\alpha}: R[x] \to R$$
>is called **<span style="color:#38ffa9">evaluation homomorphism at $\alpha$</span>**.

^4ffc7e

## The Division Algorithm

^55919d

>[!theorem] Theorem Division Algorithm ([[../../../../PDFs/judson2022.pdf#page=224|Source]])
>Let $p(x), g(x) \in F[x]$ with $F$ being a [[1 - Algebraic Structures#^a17f1c|field]] and $g(x)\neq 0$. Then **<span style="color:#38ffa9">there exist unique polynomials $q(x),r(x) \in F[x]$</span>** such that
>$$p(x)=g(x)q(x)+r(x)$$
>where $\text{deg }r(x)<\text{deg }g(x)$ or $\text{deg }r(x)=0$.
>>[!remark] Remark on Terminology
>> We call
>> - $g(x)$ the **<span style="color:#e9ffad">quotient of $f(x)$</span>**
>> - $r(x)$ the **<span style="color:#e9ffad">residue with respect to the quotient $g(x)$</span>**
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
>>Since $F$ is a [[1 - Algebraic Structures#^a17f1c|Field]] the inverse with respect to multiplication exists. We choose $r(x)=0$ and find
>>$$a = b(b^{-1}a) + 0 \tag*{$\checkmark$}$$
>><u>Inductionstep:</u>
>>We now assume, that the hypothesis is true for any $f$ with $\text{deg }f(x)<n$. We denote 
>>$$\begin{align}
>> f(x) &= a_{n}x^n+ \dots+a_{1}x+a_{0} 
>> \end{align}$$
>>$$\begin{align}
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

>[!lemma] Corollary Polynomial Factorization over Roots ([[../../../../PDFs/judson2022.pdf#page=226|Source]])
>Let $F$ be a [[1 - Algebraic Structures#^a17f1c|field]]. An element $\alpha \in F$ is a **<span style="color:#3884ff">zero</span>** or **<span style="color:#3884ff">root</span>** of  $p(x)\in F[x]$ **if and only if** $(x-\alpha)$ is a factor of $p(x)\in F[x]$
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

>[!lemma] Corollary Relation of Number of Roots and Degree of a Polynomial ([[../../../../PDFs/judson2022.pdf#page=226|Source]])
>Let $F$ be a [[1 - Algebraic Structures#^a17f1c|field]]. A polynomial $p(x)\neq 0$ with $\text{deg }p(x)=n$ in $F[x]$ can have at most $n$ distinct zeros in $F$.
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
>>with $q(x)\in F[x]$. By the [[#^b25d21|proposition of integral domain products]], which can be used since a [[1 - Algebraic Structures#^a17f1c|field]] is an extension of a [[1 - Algebraic Structures#^f48d09|integral domain]], we know
>>$$\text{deg }q(x)= n-1$$
>>Now, assume $\beta \in F$ is another root of $p(x)$ different from $\alpha$. We map as follows
>>$$p(\beta)=(\beta-\alpha)q(\beta)=0$$
>>Since, $\alpha \neq \beta$ then it must follow that $q(\beta)=0$ because of the property of [[1 - Algebraic Structures#^f48d09|integral domains]]. Therefore, $q(x)$ can have at most $n-1$ different roots different from $\alpha$. This results in $p(x)$ having at most $n$ roots, which establishes the corollary. $$\tag*{$\square$}$$

>[!def] Definition Greatest Common Divisor for Polynomials ([[../../../../PDFs/judson2022.pdf#page=226|Source]])
>Let $F$ be a [[1 - Algebraic Structures#^a17f1c|field]]. A **<span style="color:#38ffa9">monic polynomial $d(x)$</span>** is a **<span style="color:#38ffa9">greatest common divisor</span>** of polynomials $p(x),q(x) \in F[x]$ if $d(x)$ evenly divides both $p(x)$ and $q(x)$.
>
>We denote the **<span style="color:#38ffa9">greatest common divisor</span>** as
>$$\text{gcd}\Big(p(x), q(x)\Big)=d(x)$$
>
>>[!remark]- Remark on Properties of Divisors of $p(x)$ and $q(x)$ and their $\text{gcd}$
>>Furthermore, it must hold true for some $d'(x)\in F[x]$
>>$$d'(x)\;|\; p(x) \land d'(x) \;|\; q(x) \iff d'(x) \;|\; d(x)$$
>>The notation $a \;|\; b$ represents *$a$ divides $b$*.
>>(without proof)

^7eb2dc

>[!def] Definition Coprimality of Polynomials ([[../../../../PDFs/judson2022.pdf#page=226|Source]])
>Let $F$ be a [[1 - Algebraic Structures#^a17f1c|field]]. Polynomials $p(x),q(x) \in F[x]$ are **<span style="color:#38ffa9">coprime/relatively prime to each other</span>** if 
>$$\text{gcd}\Big(p(x), q(x)\Big)=1$$

^53310b

>[!lemma] Lemma of Bezout for Polynomials ([[../../../../PDFs/judson2022.pdf#page=226|Source]])
> Let $F$ be a [[1 - Algebraic Structures#^a17f1c|field]] and suppose that $d(x)$ is a [[#^7eb2dc|greatest common divisor]] of two polynomials $p(x)$ and $q(x)$ in $F[x]$. Then **<span style="color:#3884ff">there exist</span>** polynomials $r(x)$ and $s(x)$ such that
> $$d(x)=r(x)p(x)+s(x)q(x)$$
> Furthermore, the greatest common divisor of two polynomials is **<span style="color:#3884ff">unique</span>**.
>>[!proof]-
>>1. <u>Preparation:</u>
>>Denote the set
>>$$S=\Big\{ f(x)p(x)+g(x)q(x) \mid f(x),g(x) \in F[x] \Big\}$$
>>and let
>>$$\underset{d'(x) \in S}{\min} \text{deg }d'(x) = d(x)$$
>>be the [[#^a2163f|monic]] with smallest degree in $S$. Hence, we can write
>>$$d(x)=r(x)p(x)+s(x)q(x)$$
>>for some polynomials $r(x),s(x)\in F[x]$<br><br>
>>
>>2. <u>Divisibility of $p(x)$ and $q(x)$ by $d(x)$:</u>
>>We first show that $d(x) \;|\; p(x)$, therefore by the [[#^f8881d|division algorithm]] there exist polynomials $a(x),b(x)$ such that
>>$$p(x)= a(x)d(x)+b(x)$$
>>where $b(x)$ denotes the *residue polynomial* with $\text{deg } b(x) < \text{deg } d(x)$ or $\text{deg }b(x)=0$.
>>$$p(x)= a(x)d(x)+b(x) \iff b(x)=p(x)-a(x)d(x)$$
>>We can transform to
>>$$\begin{align}
>> b(x)&=p(x)-a(x){\color{#73a9ff} d(x) } \\
>> &= p(x)-a(x)\underbrace{ \Big({\color{#73a9ff}r(x)p(x)+s(x)q(x)}\Big) }_{ =d(x) }  \\
>> &= {\color{#ff73a2} p(x) }- a(x){\color{#73a9ff} r(x)}{\color{#ff73a2} p(x) } -a(x){\color{#73a9ff} s(x) q(x)} \\
>>&={\color{#ff73a2} p(x) }\underbrace{ \Big(1-a(x)r(x)\Big) }_{ \widehat{=}f(x) }-{\color{#f6ff73} q(x) }\underbrace{ \Big(a(x)s(x)\Big) }_{ \widehat{=} g(x) }
>>\end{align}$$
>> Because we chose $d(x)$ to be of smallest degree and by the [[#^55919d|division algorithm]] we have the property $\text{deg }b(x)<\text{deg }d(x)$ we can conclude $b(x)=0$. Hence, the *residue with respect to $d(x)$* is $0$ and we conclude $d(x) \;|\; p(x)$.  By the same logic we also get $d(x) \;|\;q(x)$. <br><br>
>>
>>3. <u>Showing $\text{gcd}(p(x),q(x))= d(x)$:</u>
>>Suppose there is another divisor
>>$$\text{gcd}\Big(p(x),q(x)\Big)=d'(x)$$
>>>[!note]- Logic
>>>By the [[#^7eb2dc|definition of greatest common divisors]] we know, that if $d(x)$ is a greatest common divisor, then any other common divisor $\widehat{d}(x)$ has the property
>>>$$\widehat{d}(x) \;|\; d(x)$$
>>> We want to show that
>>> $$\widehat{d}(x)|d(x) \implies \text{gcd}\Big(p(x),q(x)\Big)=d(x)$$
>>>
>>
>>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Since, $d'(x)$ is a divisor of $p(x),q(x)$ there exist $u(x),v(x) \in F[x]$ such that
>>$$\begin{align}
>> p(x) &= u(x)d'(x) \\
>> q(x) &= v(x)d'(x)
>>\end{align}$$
>>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Therefore, we get
>>$$\begin{align}
>> d(x) &= r(x){\color{#73a9ff} p(x) } + s(x){\color{#ff73a2} q(x) } \\
>> &= r(x){\color{#73a9ff} u(x)d'(x) } + s(x){\color{#ff73a2} v(x)d'(x) } \\
>> &= d'(x)\Big(r(x)u(x)+s(x)v(x)\Big) \\
>> \implies \frac{d(x)}{d'(x)} &= r(x)u(x)+s(x)v(x)
>>\end{align}$$
>>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Hence,
>>$$d'(x)|d(x) \implies \text{gcd}\Big(p(x),q(x)\Big)=d(x)$$
>>
>>4. <u>Uniqueness of the greatest common divisor</u>:
>>Suppose that $d'(x)$ is another greatest common divisor with
>>$$d'(x) = \text{gcd}\Big(p(x),q(x)\Big)=d(x)$$
>>We previously have already derived that
>>$$\begin{align}
>>d(x) = d'(x)\Big(r(x)u(x)+s(x)v(x)\Big) 
>>\end{align}$$
>>Therefore by the [[#^b25d21|degree of integral domain products]]
>>$$\text{deg }d(x) = \text{deg } d'(x) + \text{deg }\Big[r(x)u(x)+s(x)v(x)\Big]$$
>>Since both $d(x),d'(x)$ are supposed to be greatest common divisors, we get
>>$$\text{deg } d(x) = \text{deg } d'(x)$$
>>Concluding, both polynomials $d(x), d'(x)$ are of **the same degree and monic** and therefore we get
>>$$d(x)=d'(x)$$
>>which establishes the lemma. $$\tag*{$\square$}$$

## Irreducible Polynomials

>[!def] Definition Irreducible Polynomials ([[../../../../PDFs/judson2022.pdf#page=227|Source]])
>Let $F$ be a [[1 - Algebraic Structures#^a17f1c|field]] and *non-constant* $f(x) \in F[x]$ a. The polynomial $f(x)$ is called **<span style="color:#38ffa9">irreducible polynom</span>** if $f(x)$ cannot be expressed as a product of two other polynomials $g(x),h(x) \in F[x]$. 
>>[!remark] Remark on Terminology
>>Irreducible polynomials function as **<span style="color:#e9ffad">prime numbers of polynomial rings</span>**.
>
>>[!example]-
>><u>Irreducible Polynomials:</u>
>>- $x^2 - x \in \mathbb{Q}[x]$
>>- $x^2+1 \in \mathbb{R}[x]$
>>- $x^3+x^2+2 \in \mathbb{Z}_{3}[x]$ 

^22fa43


>[!property] Property of Irreducible Polynomials
>Let $F$ be a [[1 - Algebraic Structures#^a17f1c|field]], $p(x)\in F[x]$ an [[#^22fa43|irreducible polynomial]] and $q(x)\in F[x]$ 
>$$\text{gcd}\Big(p(x),q(x)\Big)=1$$
>>[!proof]-
>>Since $p(x)$ has no factors my [[#^22fa43|definition]], $p(x)$ and $q(x)$ are [[#^53310b|coprime]]. Therefore $$\text{gcd}\Big(p(x),q(x)\Big)=1 \tag*{$\square$}$$ 

>[!lemma] Lemma Integer Polynomial Representation of Rational Polynomials ([[../../../../PDFs/judson2022.pdf#page=228|Source]]) 
>Let $p(x) \in \mathbb{Q}[x]$, then
>$$p(x)= \frac{r}{s}(a_{0}+a_{1}x+\dots+a_{n}x^n)$$
>where $r,s,a_{0},\dots,a_{n} \in \mathbb{Z}$ and the $a_{i}$ are **relatively prime**, and $r$ and $s$ are **relatively prime**.
>>[!proof]-
>>Suppose 
>>$$p(x)= \frac{b_{0}}{c_{0}}+\frac{b_{1}}{c_{1}}x+\dots+\frac{b_{n}}{c_{n}}x^n$$
>>with $b_{i},c_{i}\in \mathbb{Z}$. We can rewrite $p(x)$ as
>>$$p(x)=\frac{1}{c_{0}\dots c_{n}}(d_{0}+d_{1}x+\dots+d_{n}x^n)$$
>>where 
>>$$\mathbb{Z}\ni d_{i}= b_{i} \prod_{\substack{0 \leq j \leq n \\j \neq i}} c_{j}$$
>>Let $d$ be the greatest common divisor of $d_{0},\dots d_{n}$ with $$d_{i}=a_{i}d$$
>>then we get
>>$$p(x)=\frac{d}{c_{0}\dots c_{n}}(a_{0}+a_{1}x+\dots+a_{n}x^n)$$
>>By construction the coefficients $a_{0}\dots a_{n}$ are relatively prime ($\checkmark$). Reducing $\frac{d}{c_{0}\dots c_{n}}$ to its lowest terms, i.e. $\frac{r}{s}$ we get
>>$$p(x)=\frac{r}{s}(a_{0}+a_{1}x+\dots+a_{n}x^n)$$
>>where $r,s$ are coprime, i.e. $\text{gcd}(r,s)=1$($\checkmark$).
>>$$\tag*{$\square$}$$

^ef2306

>[!theorem] Theorem Gauss's Lemma ([[../../../../PDFs/judson2022.pdf#page=228|Source]])
>Let $p(x) \in \mathbb{Z}[x]$ be a *monic polynomial* such that $$p(x) = \alpha(x)\beta(x)$$
>with $\alpha(x),\beta(x) \in \mathbb{Q}[x]$ and
>$$\begin{align}
> \text{deg }\alpha(x), \text{deg }\beta(x) < \text{deg }p(x)
>\end{align}$$
>**<span style="color:#38ffa9">Then</span>** $$p(x)=a(x)b(x)$$
>where **<span style="color:#38ffa9">$a(x),b(x) \in \mathbb{Z}[x]$ are monic polynomials</span>** with 
>$$\begin{align}
> \text{deg } \alpha(x)&=\text{deg }a(x) \\
>\text{deg }\beta(x)&= \text{deg }b(x)
>\end{align}$$
>>[!proof]-
>>By the [[#^ef2306|integer polynomial representation of rational polynomial lemma]] we can represent the polynomials $$\begin{alignat}{2}
>> \alpha(x)&=\frac{c_{1}}{d_{1}}(a_{0}+a_{1}x+\dots+a_{m}x^{m})&&=\frac{c_{1}}{d_{1}}\alpha_{1}(x) \\
>>\beta(x)&=\frac{c_{2}}{d_{2}}(b_{0}+b_{1}x+\dots+b_{n}x^{n})&&=\frac{c_{2}}{d_{2}}\beta_{1}(x)
>>\end{alignat}$$
>>with the $a_{i}$ being coprime and the $b_{i}$ being coprime. We get
>>$$\begin{align}
>> p(x)&=\alpha(x)\beta(x) \\
>> &= \frac{c_{1}c_{2}}{d_{1}d_{2}}\alpha_{1}(x)\beta_{1}(x) \\
>> &= \frac{c}{d}\alpha_{1}(x)\beta_{1}(x)
>>\end{align}$$
>>with $c,d$ being in its lowest terms for $\dfrac{c}{d}$. Hence,
>>$$d\cdot p(x)=c\cdot\alpha_{1}(x)\beta_{1}(x)$$
>><u>Case $d=1$:</u>
>>Recall, $p(x)$ is a monomial, therefore,
>>$$ca_{m}b_{n}=1$$
>>which determines the leading coefficient of $p(x)$. Hence, 
>>$$c = \begin{cases}
>>1 &\implies a_{m}=b_{n}=1 \text{ or }a_{m}=b_{n}=-1\\-1 &\implies a_{m}=1 \text{ and } b_{n}=-1 \text{ or vice versa}
>>\end{cases}$$
>>For $c=1$ we can confirm for coefficients both being $1$
>>$$\begin{align}
>> \text{deg } 1 \cdot \alpha_{1}(x) &= \text{deg } \alpha(x)\\
>> \text{deg } 1 \cdot \beta_{1}(x) &= \text{deg } \beta(x)
>>\end{align}$$
>>For the case both coefficients being $-1$ we define
>>$$\begin{align}
>> p(x)&=\Big(-\alpha_{1}(x)\Big)\Big(-\beta_{1}(x)\Big) \\
>> &= a(x)b(x)
>>\end{align}$$
>>with the degree following similarly. The case $c=-1$ follows similarly as well, which confirms the theorem for the case $d=1$.
>>
>><u>Case $d \neq1$:</u>
>>Since $\text{gcd}(c,d)=1$ there must exist a prime $p$ such that
>>$$p \;|\; d \land p \nmid c$$
>>Further, notice since all $a_{i}$ are coprime, there must be at least one $a_{j}$ such that
>>$$ p \nmid a_{j}$$
>>Similarly for the $b_{i}$
>>$$p \nmid b_{k}$$
>>We now reduce the coefficients of $\alpha_{1}, \beta_{1}$ by $\text{ mod }p$ and define
>>$$\begin{align}
>> \alpha_{1}' &= \alpha_{1} \text{ mod }p \\
>> \beta_{1}' &= \beta_{1} \text{ mod } p
>>\end{align}$$
>>As a result since $p \;|\; d$ we get for $\alpha_{1}',\beta_{1}' \in \mathbb{Z}_{p}$
>>$$\alpha_{1}'\beta_{1}'=0$$
>>Since $\mathbb{Z}_{p}[x]$ is an [[1 - Algebraic Structures#^f48d09|integral domain]] either $\alpha_{1}'=0$ or $\beta_{1}'=0$, therefore the leading coefficient of $p(x)$ must be $0$ which is a contradiction to our assumption $p(x)$ being monic, which requires it to have the leading coefficient $1$. Therefore, $d=1$, which we have already discussed previously.
>>
>>This establishes the theorem. $$\tag*{$\square$}$$

^e4c803

>[!lemma] Corollary Zeros in $\mathbb{Z}$ ([[../../../../PDFs/judson2022.pdf#page=229|Source]])
>Let $$p(x)=x^n+a_{n-1}x^{n-1}+\dots+a_{0}$$
>be a polynomial with $a_{i} \in \mathbb{Z}$ and $a_{0}\neq 0$. **<center style="color:#3884ff">$p(x)$ has a [[#^4a5c83|zero]] in $\mathbb{Q} \implies p(x)$ has a [[#^4a5c83|zero]] $\alpha \in \mathbb{Z}$</center>** Furthermore, $\alpha$ divides $a_{0}$.
>>[!proof]-
>>Let $\alpha \in \mathbb{Q}$ denote a zero in $p(x)$, i.e.
>>$$p(\alpha)=0$$
>>Therefore, $p(x)$ must have a linear factor $(x-a)$. By [[#^e4c803|Gauss's lemma]] there exists some factoring in $\mathbb{Z}[x]$ such that
>>$$p(x)=(x-\alpha)\left( x^{n-1}+\dots-\frac{a_{0}}{\alpha} \right)$$
>>therefore $\alpha \;|\; a_{0}$, i.e. $\frac{a_{0}}{\alpha} \in \mathbb{Z}$. This argument can be held repeatedly, until the degree of $1$ will conclude to a root in $\mathbb{Z}$.
>>$$\tag*{$\square$}$$

>[!lemma] Proposition Number Theoretic Property of Sums over Prime Residues 
>Let $a_{1},\dots,a_{n} \in \mathbb{Z}$ and suppose a prime $p$ divides all but one of them, i.e.
>$$p \;|\; a_{1} \dots p \;|\;a_{n-1} \text{ but } p \nmid a_{n}$$
>then the sum
>$$S = \sum_{i=1}^n a_{i}$$
>is not divisible by $p$, i.e.
>$$p \nmid S$$
>>[!proof]-
>>$$\begin{align}
>> S \equiv a_{n} \;\;(\text{mod } p) \tag*{$\square$}
>>\end{align}$$

^3926b5

>[!theorem] Theorem Eisenstein's Criterion ([[../../../../PDFs/judson2022.pdf#page=229|Source]])
>Let $p$ be a prime and suppose that
>$$f(x)= a_{n}x^{n}+\dots+a_{0}$$
>is a polynomial in $\mathbb{Z}[x]$
>
>**<center style="color:#38ffa9">If $p \;|\;a_{i}$ for all $i \in\{ 0,\dots,n-1 \}$ but $p \nmid a_{n}$ and $p^2 \nmid a_{0}$, then $f(x)$ is irreducible over $\mathbb{Q}$</center>**
>>[!proof]-
>>Let $$f(x)=(x^r+\dots+b_{0})(x^s+\dots+c_{0})$$
>>be a factorization in $\mathbb{Z}[x]$ with $b_{r} \neq 0$, $c_{s}\neq 0$ and $r,s<n$. By the conditions of the theorem we know
>>$$p^2 \nmid a_{0}=b_{0}c_{0}\implies p \nmid b_{0} \lor p \nmid c_{0}$$
>>by the [[../../../../Lehre/Kryptologie/2 - Algebraische und Zahlentheoretische Grundlagen (1)#^50378b|fundamental theorem of algebra]]. Further note
>>$$p \nmid a_{n}=b_{r}c_{s} \implies p \nmid b_{r} \land p \nmid c_{s}$$
>>Summarizing, the conditions guarantee us that the leading coefficient **is not dividable by $p$** but one of the constant coefficients **must be divisible by $p$**. Without loss of generality, let $p \;|\; c_{0}$. Denote $m$ to be the smallest value of $k$ such that $$p \nmid c_{k}$$
>>then
>>$$a_{m}= b_{0}c_{m}+b_{1}c_{m-1}+\dots+b_{m}c_{0}$$
>>is not be divisible by $p$ since $b_0c_{m}$ is the only term not divisible by $p$, while the others are (by this [[#^3926b5|proposition]]), i.e.
>>$$a_{m} \equiv b_{0}c_{m} \;\;(\text{mod } p)$$
>>By our assumption that all $a_{i}$ are divisible by $p$, the index of $m = n$. Hence, there is no factorization for $f(x)$ for the given conditions.
