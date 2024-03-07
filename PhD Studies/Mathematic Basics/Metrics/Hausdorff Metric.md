>[!source]
>>[!Links]-
>>URL: http://arxiv.org/abs/1808.02574
>>PDF: [PDF](../../../PDFs/conci2018.pdf)
>>Zotero: [Zotero-Link](zotero://select/items/@conci2018)
>
>>[!ABSTRACT]-
>>The purpose of this paper is to give a survey on the notions of distance between subsets either of a metric space or of a measure space, including definitions, a classification, and a discussion of the best-known distance functions, which is followed by a review on applications used in many areas of knowledge, ranging from theoretical to practical applications.

>[!def] Definition Point Set Distance
>Let 
>- $(X,d_{X})$ be a metric space
>- $\mathcal{P}(X)$ the power set of $X$
> - $x \in X$  
> - $A \in \mathcal{P}(X)\setminus \emptyset$
> 
> then the distance between $x$ and $A$ can be given as
> $$\begin{align} 
> d: X \times \mathcal{P}(X)\setminus \emptyset \to \mathbb{R} 
>\end{align}$$  
>with
>$$ d(x,A) = \underset{a \in A}{\text{inf}} \; d_{X}(x,a)\;$$
>>[!pic]-
>>![[Figures/point_set.excalidraw|point_set.excalidraw|center]]
>
>>[!remark]- Remark Metric Axioms
>> $$\begin{alignat}{2}
>>(i)& \quad&&d(x,y) = d(y,x) \tag{Symmetry} \\
>>(ii)& \;\quad&&d(x,y) \geq 0 \text{ and } d(x,x)=0 \tag{Non-Negativeness} \\
>>(iii)& \quad &&d(x,y)=0 \Rightarrow x=y \tag{Positiveness} \\ 
>>(iv)& \quad &&d(x,y) \leq d(x,z) + d(z,y) \tag{Triangle Inequality}
>>\end{alignat}$$
>>- Symmetry ❌
>>>$$d(x,A)=\underset{a \in A}{\text{inf}}\; d_{X}(a,x)\neq d(A,x)$$
>>>Note, the function is defined such that the first argument is a point and the second argument is a set
>>
>>- Non-Negativeness ✅
>>>$$d(A,x)=\underset{a \in A}{\text{inf}}\; \underbrace{ d_{X}(a,x) }_{ \geq 0 }$$
>>>Since $d_{X}$ is a metric and is guaranteed to be non-negative, the infimum must be also non-negative
>>
>>- Positiveness ❌
>>> Clearly $x \neq A$ since $x \in X$ and $A \in \mathcal{P}(X)$. Further, there are potentially infinitely many $A \in \mathcal{P}(X)$ that hold $d(x,A) = 0$, i.e. let $A_{1}=[0,3]$, $A_{2}=[1,2]$ and $x=1$, then
>>> $$\begin{align}
>>> d(x,A_{1}) &= \underset{a \in A_{1}}{\text{inf}}\; d(a,x) = 0 \\ 
>>> d(x,A_{2}) &= \underset{a \in A_{2}}{\text{inf}}\; d(a,x) = 0
>>>\end{align}$$
>>
>>- Triangle Inequality ❌
>>> Again, since $x \in X$ and $A \in \mathcal{\mathcal{P}}(X)$, we have the problem of properly setting up the triangle inequality, i.e. let $b \in X$ and $B \in \mathcal{P}(X)$, then we have
>>> $$\begin{align}
>>> d(x,A) &\leq d(x,B) + \underbrace{ d(B,A) }_{ \text{not defined} } \\
>>> d(A,x) &\leq d(A,b) + \underbrace{ d(b,x) }_{ \text{not defined} } 
>>>\end{align}$$

^fb2589

>[!def] Definition Set to Set Distance
>Let 
>- $(X,d_{X})$ be a metric space
>- $\mathcal{P}(X)$ the power set of $X$
> - $A,B \in \mathcal{P}(X)\setminus \emptyset$
> 
> then the distance between A and B can be given as
> $$d: \mathcal{P}(X)\setminus \emptyset \times \mathcal{P}(X)\setminus \emptyset \to \mathbb{R}$$
> with
> $$d(A,B) = \underset{a \in A, b \in B}{\text{inf}}\; d_{X}(a,b)$$
>>[!pic]-
>>![[Figures/set_to_set_1.png]]
>
>>[!remark] Remark Metric Axioms
>> $$\begin{alignat}{2}
>>(i)& \quad&&d(x,y) = d(y,x) \tag{Symmetry} \\
>>(ii)& \;\quad&&d(x,y) \geq 0 \text{ and } d(x,x)=0 \tag{Non-Negativeness} \\
>>(iii)& \quad &&d(x,y)=0 \Rightarrow x=y \tag{Positiveness} \\ 
>>(iv)& \quad &&d(x,y) \leq d(x,z) + d(z,y) \tag{Triangle Inequality}
>>\end{alignat}$$
>>- Symmetry ✅
>>>$$d(A,B)=\underset{a \in A, b \in B}{\text{inf}}\; d_{X}(a,b)= d(B,A)$$
>>
>>- Non-Negativeness ✅
>>>$$d(A,B)=\underset{a \in A, b \in B}{\text{inf}}\; \underbrace{ d_{X}(a,b) }_{ \geq 0 }$$
>>>Since $d_{X}$ is a metric and is guaranteed to be non-negative, the infimum must be also non-negative
>>
>>- Positiveness ❌
>>> For a similar reason as in the [[#^fb2589| point to set distance]], we can easily construct cases, such that $d \equiv 0$ for distinct sets $A,B$. More precisely, any sets $A,B$ with $A \cap B \neq \emptyset$ have $$d(A,B) = 0$$
>>> The following example illustrates the problem. Let $A = [0,2]$ and $B = [1,3]$, then note that $A \cap B = [1,2]$. For the infimum in $\underset{a \in A, b \in B}{\text{inf}}\;d(a,b)$ we can choose any $a,b \in A \cap B$ and get
>>> $$d(A,B) = 0$$
>>> with $A \neq B$
>>
>>- Triangle Inequality ❌
>>> The following example will illustrate the issue with this property. Let again $A = [0,2]$, $B=[1,5]$, $C=[4,6]$ and $d_X$ the $p=1$ Minkowski distance, we have
>>> $$\begin{alignat}{2}
>>> d(A,C) &= \underset{a \in A, c \in C}{\text{inf}}\;d_{X}(a,c) &&= d_{X}(2,4) = 2 \\
>>> d(A,B) &= \underset{a \in A, b \in B}{\text{inf}}\;d_{X}(a,b) &&= d_{X}(1,1) = 0 \\
>>> d(B,C) &= \underset{b \in B, c \in C}{\text{inf}}\;d_{X}(b,c) &&= d_{X}(4,4) = 0 \\
>>>\end{alignat}$$
>>>Then we have for the triangle inequality
>>>$$\begin{alignat}{2}
>>> d(A,C) &\leq d(A,B) &&+ d(B,C) \\
>>> 2 &\not\leq 0 &&+ 0
>>>\end{alignat}$$



>[!def] Definition The Hausdorff Family
>Let 
>- $(X,d_{X})$ be a metric space
>- $\mathcal{P}(X)$ the power set of $X$
>
> The Hausdorff function
> $$h: \mathcal{P}(X)\setminus \emptyset \times \mathcal{P}(X)\setminus \emptyset \to \overline{\mathbb{R}}$$
> is given  $\forall A, B \in \mathcal{P}(X) \setminus \emptyset$
> $$\begin{alignat}{2}
> h(A,B) &= \underset{}{\text{max}}\;\{ \underset{a \in A}{\text{sup}}\;d_{X}(a,B)&&, \underset{b \in B}{\text{sup}} \; d_{X}(b,A)\}\\
>        &= \underset{}{\text{max}}\;\{ \underset{a \in A}{\text{sup}}\;\underset{b \in B}{\text{inf}\vphantom{\text{p}}}\;d_{X}(a,b)&&, \underset{b \in B}{\text{sup}}\;\underset{a \in A}{\text{inf}\vphantom{\text{p}}}\;d_{X}(a,b)\}
>\end{alignat}$$
>>[!remark] Remark Axiom Metrics
>> $$\begin{alignat}{2}
>>(i)& \quad&&d(x,y) = d(y,x) \tag{Symmetry} \\
>>(ii)& \;\quad&&d(x,y) \geq 0 \text{ and } d(x,x)=0 \tag{Non-Negativeness} \\
>>(iii)& \quad &&d(x,y)=0 \Rightarrow x=y \tag{Positiveness} \\ 
>>(iv)& \quad &&d(x,y) \leq d(x,z) + d(z,y) \tag{Triangle Inequality}
>>\end{alignat}$$
>>Symmetry ✅
>>> The Hausdorff function satisfies the symmetry property, since
>>> $$d(A,B) = \underset{}{\text{max}}\{ \underset{a \in A}{\text{sup}} \; d_{X}(a,B), \underset{b \in B}{\text{sup}} \; d_{X}(b, A)\}\; = d(B,A)$$
>>>The suprema inside the maximum operator are interchangeable and the maximum value will be returned regardless of the order the arguments are passed into the distance function.
>>
>>Non-Negativeness ✅
>>>Since the Hausdorff function relies on the underlying metric space $X$ and its distance function, the values are guaranteed to be at least 0
>>
>>>
>>
>>It is not a distance function, since it maps to the extended real numbers $\overline{\mathbb{R}}$ with
>>$$h(\{ 0 \}, \mathbb{R}) = + \infty$$
>>It is not a pseudo metric, because it does not satisfy property
>>$$\begin{alignat}{2}
>> (iii)& \quad &&d(x,y)=0 \Longrightarrow x=y \tag{positiveness}
>>\end{alignat}$$
>>because let $A=(0,1)$ and $B=[0,1]$, we have
>>$$h(A,B)=0$$

>[!property] Proposition
>$\forall A,B \in \mathcal{P}(X)\setminus \emptyset:$
>$$h(A,B) = \underset{x \in X}{\text{sup}} \; \lvert d(x,A)-d(x,B) \rvert \;$$
>>[!proof]
>>Let 
>>- $x \in X$
>>- $a \in A$
>>- $b \in B$
>>
>>We have
>>$$d(x,b) \leq d(x,a) + d(a,b) \tag{Triangle Inequality}$$
>>and it follows
>>$$d(x,B) = \underset{b \in B}{\text{inf}}d(x,b)\;$$
