>[!Def] Definition 1.1 $\sigma$-Field ([[../../../../../PDFs/shao2003.pdf#page=18|Source]])
>Let $\mathcal{F}$ be a collection of subsets of a sample space $\Omega$. $\mathcal{F}$ is called a $\sigma$-Field if and only if it has the following properties.
>1. $\emptyset \in \mathcal{F}$
>2. $A \in \mathcal{F} \Rightarrow A^C\in \mathcal{F}$
>3. $A_i \in F$ with $i = 1,2,\ldots \Rightarrow \bigcup A_i \in \mathcal{F}$

>[!note] Note (Measurable Space)
>$(\Omega, \mathcal{F})$ is also called a _measurable space_.

>[!Def] Definition 1.2 Borel $\sigma$-Field  ([[../../../../../PDFs/shao2003.pdf#page=18|Source]])
> Let $\mathcal{C}$ be the collection of all open intervals on $\mathbb{R}$. Then $\mathcal{B}(\mathbb{R}) = \sigma(C)$ is called the <u>Borel $\sigma$-Field</u>
> The elements of $\mathcal{B}$ are called *Borel Sets*.
> ^def12

>[!Def] Definition 1.3 Measure  ([[../../../../../PDFs/shao2003.pdf#page=19|Source]]) 
>Let $(\Omega, \mathcal{F})$ be a _measurable space_. A set function $\nu$ defined on $\mathcal{F}$ is called a *measure* if and only if it has the following properties.
>1. $0\leq \nu(A) \leq \infty \quad \forall A\in \mathcal{F}$
>2. $\nu(\emptyset) = 0$
>3. If $A_i \in \mathcal{F}$ with $i=1,2, \ldots$ and $A_i$ are disjoint, then
> $$\nu\left(\bigcup_{i=1}^\infty A_i\right) = \sum_{i=1}^\infty \nu\left(A_i\right)$$
> 
>>[!example]- Example: Counting Measure
>>Let $\Omega$ be a sample space, $\mathcal{F}$ the collection of all subsets, and $\nu(A)$ the number of elements in $A \in \mathcal{F}$. Further, we agree on if $\lvert A \rvert = \infty$ that $\nu(A)=\infty$. Then $\nu$ is a measure on $\mathcal{F}$ and is called the _counting measure_.
>
>>[!example]- Example: Lebesgue Measure
>>There is a unique measure $m$ on $(\mathbb{R}, \mathcal{B})$ that satisfies $$m([a,b])=b-a$$ for every finite interval $[a,b]$ with $-\infty<a \leq b < \infty$. This is called the _Lebesgue measure_. If we restrict $m$ to be the measurable space $([0,1], \mathcal{B}_{[0,1]})$, then $m$ is a probability measure.
> ^def13



>[!note]- Note (Measure and Probability Space)
>1. $(\Omega, \mathcal{F}, \nu)$ is called a <u>measure space</u>
>2. If $\nu(\Omega) = P(\Omega) =  1$, then $(\Omega, \mathcal{F}, P)$ is called a <u>probability space</u> and $P$ is called a <u>probability measure</u>

>[!Note]- Arithmetic with infinity
>$\forall x \in \mathbb{R}$ we have
>1. $\infty + x = \infty$
>2. $x \cdot \infty = \infty$ with $x >0$
>3. $x \cdot \infty = -\infty$ with $x <0$
>4. $0 \cdot \infty = 0$
>5. $\infty + \infty = \infty$
>6. $\infty^a = \infty$ with $a > 0$
>
>The following **are not defined**
>1. $\infty - \infty \Rightarrow$ not defined
>2. $\frac{\infty}{\infty} \Rightarrow$ not defined

>[!Example]- Examples on Measure Functions $\nu$
>>[!Example] Example $(1)$ Counting Measure
>>Let 
>>- $\Omega$ be a sample space
>>- $\mathcal{F}$ be a collection of all subsets
>>
>> The measure function $\nu(A)$ counts the number of elements of the subset $A \in \mathcal{F}$
>> => According to [[Chapter 1 Probability Theory Notes#^def13|Definition 1.3]] the  <u>counting measure</u> is a measure function. $\square$
>
>>[!Example] Example $(2)$ Lebesgue Measure
>> Let
>> - $(\mathbb{R}, \mathcal{B})$ be a measurable space with $\mathcal{B}$ being a *Borel $\sigma$-Field* according to [[Chapter 1 Probability Theory Notes#^def12|Definition 1.2]]
>> Then there is a unique measure $m$ on $(\mathbb{R}, \mathcal{B})$ that satisfies
>> $$ m([a,b]) = b-a $$
>> for every finite interval $[a,b]$, with $-\infty < a \leq b < \infty$. This is called the <u>Lebesgue measure</u>.
>>>[!note]-
>>>If $m$ is restricted to the measurable space $([0,1], \mathcal{B}_{[0,1]}$, then $m$ is a <u>probability measure</u>

>[!Def] Proposition 1.1 ([[../../../../../PDFs/shao2003.pdf#page=20|Source]])
>Let $(\Omega, \mathcal{F}, \nu)$ be a measure space
>1. For $A,B \in \mathcal{F}$ 
>$$\begin{align} A \subset B \Rightarrow \nu(A) \leq \nu(B) \tag{Monotonicity}\end{align}$$
>
>>[!proof]-
>>Since $A \subset B$ it follows $B= A \cup (A^C \cap B)$ and $A$ and $A^C \cap B$ are disjoint.
>>![[Figure1_1]]
>>By [[Chapter 1 Probability Theory Notes#^def13| Definition 1.3.3]] we have 
>>$$\nu(B) = \nu(A) + \nu(A^C \cap B)$$
>>which is no smaller than $\nu(A)$ since $\nu(A^C \cap B) \geq 0$ by [[Chapter 1 Probability Theory Notes#^def13| Definition 1.3.1]] $\square$
>
>2. For any sequence $A_1, A_2, \ldots$
>$$\begin{align} \nu\left(\bigcup_{i=1}^\infty A_i\right) \leq \sum_{i=1}^\infty \nu(A_i) \tag{Subadditivity}\end{align}$$
>
>>[!proof]-
>>Assuming $A_i$ are disjoint, i.e. $A_i \cap A_j = \emptyset$ for $1 \leq i < j \leq \infty$ then [[Chapter 1 Probability Theory Notes#^def13|Definition 1.3.3]] holds.
>>Assuming $A_i$ are not disjoint, i.e.  $A_i \cap A_j \neq \emptyset$ for $1 \leq i < j \leq \infty$
>>We construct a sequence $(B_i)_{i=1}$ with
>>$$B_i = A_i \setminus \left( \bigcup_{j>i}^\infty A_j \cap A_i \right) $$
>>Since the $B_i$'s are disjoint, we can state according to [[Chapter 1 Probability Theory Notes#^def13|Definition 1.3.3]]
>>$$\nu\left(\bigcup_{i=1}^\infty B_i\right) = \sum_{i=1}^\infty \nu\left(B_i\right)$$
>>Further note $\bigcup_{i=1}^\infty B_i = \bigcup_{i=1}^\infty A_i$ by construction, we have
>>$$ \begin{align}\nu\left(\bigcup_{i=1}^\infty B_i\right) &= \sum_{i=1}^\infty\nu(B_i)\\&= \nu\left(\bigcup_{i=1}^\infty A_i\right)\end{align}$$
>>Note there that there exist some $B_k \subset A_k$ by construction of disjointing the $B_i$, thus
>>$$ \nu(B_k) \leq \nu(A_k) \Rightarrow \sum_{i=1}^\infty\nu(B_i) \leq \sum_{i=1}^\infty\nu(A_i)$$
>>Hence,
>>$$\sum_{i=1}^\infty\nu(B_i) = \nu\left(\bigcup_{i=1}^\infty A_i\right) \leq \sum_{i=1}^\infty\nu(A_i) \tag*{$\square$}$$ 
>
>3. If $A_1 \subset A_2 \subset A_3 \subset \ldots$ (or $A_1 \supset A_2 \supset A_3 \supset \ldots$ and $\nu(A_1) < \infty$), then
>$$\begin{align} \nu\left(\lim_{n \rightarrow\infty} A_n\right) = \lim_{n \rightarrow \infty} \nu(A_n)\end{align}$$ with
>$$\begin{align} \lim_{n\rightarrow \infty} A_n = \bigcup_{i=1}^\infty A_i \qquad\Bigg( \text{or} = \bigcap_{i=1}^\infty A_i \Bigg) \tag{Continuity}\end{align}$$
>
>>[!proof]-
>>We have 
>>$$ \begin{align}
>>\nu\left(\lim_{i \to \infty} A_i\right) &= \nu\left(\bigcup_{n=1}^\infty A_n\right)\\ 
>>&=\lim_{n \to \infty} \nu\left(\bigcup_{i=1}^n A_i\right) \\
>>&= \lim_{n \to \infty}\nu(A_n) \tag*{$\square$} 
>>\end{align}$$
>>
>>The decreasing sequence follows from using the complement of $A$.


>[!def] Definition 1.4 Cumulative Distribution Function (CDF) ([[../../../../../PDFs/shao2003.pdf#page=20|Source]])
> The CDF of a probability measure $P$ is defined as
> $$F(x) = P\Big((-\infty, x]\Big)$$
> with $x \in \mathbb{R}$

>[!def] Proposition 1.2 ([[../../../../../PDFs/shao2003.pdf#page=20|Source]])
>1. Let $F$ be a CDF on $\mathbb{R}$, then
>	1. $F(-\infty) = \lim_{x\to - \infty}F(x) = 0$
>	2. $F(\infty) = \lim_{x\to \infty}F(x) = 1$
>	3. $F$ is non-decreasing, i.e., $F(x) \leq F(y)$ if $x \leq y$
>	4. $F$ is right continuous, i.e.  $$\lim_{y \to x, y >x} F(y) = F(x)$$
>2. Suppose that a real-valued function $F$ on $\mathbb{R}$ satisfies Proposition 1.2 $(1)$, then $F$ is the CDF of a unique probability measure on $(\mathbb{R},\mathcal{B})$