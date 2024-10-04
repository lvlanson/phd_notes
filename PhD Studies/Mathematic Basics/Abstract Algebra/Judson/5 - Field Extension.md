>[!def] Definition Extension Field ([[../../../../PDFs/judson2022.pdf#page=272|Source]])
> Let $F$ denote a [[1 - Algebraic Structures#^a17f1c|field]]. We say $E$ is a **<span style="color:#38ffa9">field extension $E/F$</span>** of $F$ if $F$ is a subfield of $E$, i.e.
> $$F \subset E$$ 
>>[!example] $\mathbb{C}/\mathbb{R}$ is a field extension
>
>>[!example] $\mathbb{R}/\mathbb{Q}$ is a field extension

^d39ed6

>[!def] Definition Degree/Index/Relative Degree of an Extension Field ([Source](https://mathworld.wolfram.com/ExtensionField.html))
>The **<span style="color:#38ffa9">degree of an extension field $F/E$</span>** denoted as **<span style="color:#38ffa9">$[\mathbb{K}:\mathbb{F}]$</span>** is the dimension of $\mathbb{K}$ as a vector space $\mathbb{F}$, i.e.
>$$[\mathbb{K}:\mathbb{F}] = \text{dim}_{\mathbb{F}} \mathbb{K}$$

>[!def] Definition Algebraic Elements of Extensions Fields ([[../../../../PDFs/judson2022.pdf#page=274|Source]])
>Let $E/F$ be an [[#^d39ed6|extension field]] and $\alpha \in E$. We say **<span style="color:#38ffa9">$\alpha$ is algebraic over $F$</span>** if
>$$f(\alpha)=0$$
>for some polynomial $f \in F[x]$ with $f \neq 0$.
>>[!example]
>>We denote 
>>- $E=\mathbb{R}$
>>- $F=\mathbb{Q}$
>>
>>then $\alpha=\sqrt{ 2 } \in E$ is algebraic over $F$, because
>>$$f(x)=x^2-2 \implies f\left(\sqrt{ 2 }\right)=\left(\sqrt{ 2 }\right)^2-2=0$$

^5451ab

>[!def] Definition Transcendental Elements of Extension Fields ([[../../../../PDFs/judson2022.pdf#page=272|Source]])
>Let $E/F$ be an [[#^d39ed6|extension field]] and $\alpha \in E$. **<span style="color:#38ffa9">If $\alpha \in E$ is not algebraic</span>**, then it is transcendental over $F$.


>[!def] Definition Algebraic Extension ([[../../../../PDFs/judson2022.pdf#page=274|Source]])
>Let $E/F$ be an [[#^d39ed6|extension field]]. We say **<span style="color:#38ffa9">$E/F$ is an algebraic extension</span>**, if every element in $E$ is algebraic over $F$.

>[!def] Definition Simple Extension ([[../../../../PDFs/judson2022.pdf#page=274|Source]])
>Let $E/F$ be an [[#^d39ed6|extension field]] and $\alpha \in E$. If
>$$E=F(\alpha)$$
>then we call $E$ **<span style="color:#38ffa9">simple extension of $F$</span>**.

>[!theorem] Theorem Existence and Uniqueness of Polynoms of Algebraic Elements ([[../../../../PDFs/judson2022.pdf#page=275|Source]])
>Let $E$ be an [[#^d39ed6|extension field]] of a field $F$ and $\alpha \in E$ with $\alpha$ being [[#^5451ab|algebraic]] over $F$. 
>
>Then **<span style="color:#38ffa9">there exists a unique [[2 - Polynomial Rings#^22fa43|irreducible]] [[2 - Polynomial Rings#^a2163f|monic]] polynomial $p(x) \in F[x]$ of smallest degree</span>** such that $$p(\alpha)=0$$ If $f(x)$ is another polynomial in $F[x]$ such that $f(\alpha)=0$, then $p(x)$ divides $f(x)$.
>>[!proof]
>> Let $$\phi_{\alpha}:F[x] \to E$$
>> denote the [[2 - Polynomial Rings#^4ffc7e|evaluation homomorphism]]