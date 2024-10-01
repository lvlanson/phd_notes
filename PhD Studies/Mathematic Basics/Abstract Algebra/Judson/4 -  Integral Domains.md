>[!remark] Remark: Motivation on Field of Fractions ([[../../../../PDFs/judson2022.pdf#page=237|Source]])
>Every field is also an integral domain; however, there are many [[../Judson/1 - Algebraic Structures#^f48d09|integral domains]] that are not [[../Judson/1 - Algebraic Structures#^a17f1c|fields]]. For example, the integers $\mathbb{Z}$ form an [[../Judson/1 - Algebraic Structures#^f48d09|integral domain]] but not a [[../Judson/1 - Algebraic Structures#^a17f1c|field]]. 
>
>A question that naturally arises is how we might associate an integral domain with a field. There is a natural way to construct the rationals $\mathbb{Q}$ from the integers: the rationals can be represented as formal quotients of two integers, i.e. $a,b \in \mathbb{Z}$ we have $\frac{a}{b} \in \mathbb{Q}$. The rational numbers are certainly a field. In fact, it can be shown that the rationals are the smallest field that contains the integers. 
>
>Given an integral domain $D$, our question now becomes how to construct a smallest field $F$ containing $D$. We will do this in the same way as we constructed the rationals from the integers.
>
>Ongoing we will denote a fraction for $a,b \in D$ with $D$ being an [[1 - Algebraic Structures#^f48d09|integral domain]] as elements of $D\times D$, i.e.
>$$\frac{a}{b}: \iff (a,b)$$
>to more clearly define equivalent elements and avoid that $b \neq 0$.

>[!Lemma] Lemma Equivalence Relation on Cross Products of Integral Domains ([[../../../../PDFs/judson2022.pdf#page=237|Source]])
>Denote the set of all fractions on $D$  as
>$$S=\{ (a,b) \mid a,b \in D \land b \neq 0 \}$$
>Further, we define a relation on $S$ with
>$$(a,b) \sim (c,d) \implies ad=bc$$
>The given **<span style="color:#3884ff">relation defines an equivalence relation</span>**.
>>[!proof]-
>>Let all tuples be of the form $(x,y)$ with $x,y \in D$ and $y \neq 0$
>>1. <u>Reflexivity:</u>
>>Since $D$ is a [[1 - Algebraic Structures#^f48d09|integral domain]] it is commutative, hence
>>$$(a,b) \sim (b,a) \implies ab=ba \tag*{$\checkmark$}$$
>>2. <u>Symmetry:</u>
>>$$(a,b) \sim (c,d) \iff ad=bc \iff bc=ad \iff (c,d) \sim (a,b) \tag*{$\checkmark$}$$
>>3. <u>Transitivity:</u>
>>$$\begin{align}
>> (a,b) \sim (c,d) \land (c,d) \sim (e,f)  &\iff \underbrace{ ad=bc }_{ \cdot f } \land cf=de   \\
>> &\iff adf = b{\color{#85b3ff}cf} \land {\color{#85b3ff}cf} = de \\
>> &\iff a{\color{#85b3ff}d}f = b{\color{#85b3ff}d}e \land cf=de \\
>> &\implies af = be  \\
>> &\implies (a,b) \sim(e,f) \tag*{$\checkmark$}
>>\end{align}$$
>>This establishes the lemma. $$\tag*{$\square$}$$

^825be9

>[!lemma] Lemma Operations of Addition and Multiplication are Well-Defined on [[#^825be9|the Set of All Fractions]] ([[../../../../PDFs/judson2022.pdf#page=238|Source]])
>Let $(a,b),(c,d) \in S$
>
>Define **<span style="color:#3884ff">addition</span>**:
>$$(a,b)+(c,d)=(a+c,bd)$$
>
>Define **<span style="color:#3884ff">multiplication</span>**:
>$$(a,b)\cdot(c,d)=(ac,bd)$$
>
>**<span style="color:#3884ff">Both operations are closed on $S$.</span>**
>>[!proof] Proof omitted

^4311dc

>[!lemma] Lemma The Set of All Fractions forms a Field ([[../../../../PDFs/judson2022.pdf#page=238|Source]])
>Let $S$ be the set of all fractions defined over the [[#^825be9|equivalence relation]] $\sim$ on the integral domain $D$. Together with the [[#^4311dc|previously defined operations]], **<span style="color:#3884ff">the set $S$ forms a field $(S,+,\cdot)$</span>**. 
>
>>[!remark] Remark: Ongoing we will denote $S$ as <u>Field of Fractions</u> with $S=F_{D}$
>
>>[!proof]-
>>Let $(a,b), (c,d), (e,f) \in F_{D}$ with $b,d,f \neq 0$
>>1. $(F_{D},+)$ is a commutative group:
>> - Associativity: $$\begin{align}
>> \Big[(a,b)+(c,d)\Big]+(e,f) &= (a+d,cb)+(e,f) \\
>> &= (a+d+f,cbe) \\
>> &= (a,b)+(d+f,ce) \\
>> &= (a,b) \Big[(d,e)+(f,e)\Big]  
>>\end{align}$$
>>- Neutral Element: $e=(0,1)$
>>$$\begin{align}
>> (0,1)+(a,b)=(a,b)+(0,1)&=(a+0,b \cdot 1) \\
>>    &=(a,b)
>>\end{align}$$
>>- Inverse Element:  $-(a,b)=(-a,b)$ $$(a,b)+(-a,b)=(-a,b)+(a,b)=(a-a,bb)=(0,b^2)\sim(0,1)=e$$
>>- Commutativity:
>>$$(a,b) +(c,d)=(a+c,bd)=(c+a,db)=(c,d)+(a,b) \tag*{$\checkmark$}$$
>>2. $(F_{D}\setminus \{ (0,1) \})$ is a commutative group:
>>- Associativity:$$\begin{align}
>> \Big[(a,b)\cdot(c,d)\Big]\cdot(e,f)&= (ac,bd)\cdot(e,f) \\
>> &= (ace,bdf) \\
>> &= (ab) \cdot(ce,df) \\
>> &= (ab) \cdot \Big[(c,d)\cdot (e,f)\Big]
>>\end{align}$$
>>- Neutral Element: $e=(1,1)$ $$\begin{align}
>> (a,b) \cdot (1,1) = (1,1) \cdot (a,b) &= (1 \cdot a, 1 \cdot b) \\
>> &= (a,b)
>>\end{align}$$
>>- Inverse Element: $(a,b)^{-1}=(b,a)$ $$(a,b)\cdot(b,a)=(b,a) \cdot (a,b)= (ab,ab) \sim(1,1)=e$$
>>- Commutativity: $$(a,b) \cdot (c,d)=(ac,bd)=(ca,db)=(c,d) \cdot (a,b) \tag*{$\checkmark$}$$
>> This verifies the lemma and establishes $F_{D}$ as a field $$\tag*{$\square$}$$
>
