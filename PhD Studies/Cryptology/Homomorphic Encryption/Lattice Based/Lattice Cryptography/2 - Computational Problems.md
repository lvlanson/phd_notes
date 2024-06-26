>[!def] Definition Shortest Vector Problem (SVP) ([[../../../../../PDFs/sabani2024.pdf#page=6|Source]])
>
>Given a basis $\mathbf{B}=\{\mathbf{b}_{1}, \mathbf{b}_{2},\dots,\mathbf{b}_{n}  \}$ of a lattice $\mathcal{L}(\mathbf{B})$, find the nonzero shortest vector $\mathbf{v}$, i.e., find $\mathbf{v} \in \mathcal{L}$ for which $$\lvert\lvert \mathbf{v} \rvert\rvert = \lambda_{1}(\mathcal{L}) $$
>where $\lambda_{1}$ denotes the [[1 - Elementary Definitions#^5efb92|minimum distance of a lattice]].
>>[!pic] Illustration
>>![[../Figures/shortest_vector_problem.png|center| 450]]
>

>[!theorem] Minkowski's First Theorem ([[../../../../../PDFs/sabani2024.pdf#page=6|Source]])
>The shortest nonzero vector in any $n$-dimensional lattice $\mathcal{L}$ has a length, at most, of $$\gamma_{n}\det(\mathcal{L})^{1/n}$$ where $\gamma_{n}$ is an absolute constant (approximately equals to $\sqrt{ n }$) that only depends on the dimension $n$ and $\det(\mathcal{L})$ is the determinant of the lattice.

>[!def] Definition Gap Shortest Vector Problem ($\text{GAPSVP}_{\gamma})$ ([[../../../../../PDFs/sabani2024.pdf#page=6|Source]])
>Let $\mathcal{L}$ be an $n$-dimensional lattice and $d$ a positive number and an instance (a decision problem) of $\text{GAPSVP}_{\gamma}$ is given. The response of the instance is given as
>$$\text{GAPSVP}_{\gamma}(d)=\begin{cases}
> \text{YES} & \lambda_{1}(\mathcal{L}) \leq d \\
> \text{NO} & \lambda_{1}(\mathcal{L})>\gamma(n) \cdot d
>\end{cases}$$
>>[!Note]- Note on the Gap
>> There is a **gap** in the range $$\Big(d, \gamma(n)\cdot d \Big]$$ where no decision is made. One could say, this range is not part of domain of the $\text{GAPSVP}_{\gamma}$ instance.
>
>>[!pic] Illustration
>>![[../Figures/gapsvp.png|center|300]]
>>The gap is given by the area between the two circle. Given some $d$ outside the outer circle, NO is given by the instance, given some $d$ inside the inner circle, YES is given by the instance. The area inbetween won't give a response.

^02fc56

>[!def] Definition Closest Vector Problem (SVP) ([[../../../../../PDFs/sabani2024.pdf#page=7|Source]])
> Given a basis $\mathbf{B}=\{ \mathbf{b}_{1}, \mathbf{b}_{2}, \dots, \mathbf{b}_{n} \}$ of a lattice $\mathcal{L}(\mathbf{B})$ and a target vector $t$, not necessarily in the lattice, find the lattice point $\mathbf{v} \in \mathcal{L}(\mathbf{B})$ closest to $\mathbf{t}$, i.e.
> $$d(t,\mathcal{L}): \min_{\mathbf{x} \in \mathcal{L}} \lvert\lvert \mathbf{x}-\mathbf{t} \rvert\rvert $$
>
>>[!pic] Illustration
>> ![[../Figures/closest_vector_problem.png | center | 300]]
>

^08199f

>[!def] $\gamma$-Approximate Closest Vector Problem (CVP) ([[../../../../../PDFs/sabani2024.pdf#page=8|Source]])
> Given a basis $\mathbf{B}=\{ \mathbf{b}_{1}, \mathbf{b}_{2}, \dots, \mathbf{b}_{n} \}$ of a lattice $\mathcal{L}(\mathbf{B}) \subset \mathbb{R}^n$ and a point $\mathbf{t} \in \mathbb{R}^n$, find a lattice point $\mathbf{v}\in \mathcal{L}$ such that $$\lvert\lvert \mathbf{t}-\mathbf{v} \rvert\rvert \leq \gamma(n) \cdot d(t, \mathcal{L})$$
>
>>[!remark]
>>Similarly to the [[#^08199f| closest vector problem]] we are looking for a vector which is approximately close up to a factor of $\gamma(n)$.


>[!observation] Conjecture Quantum-Security ([[../../../../../PDFs/sabani2024.pdf#page=10|Source]])
>---
>**There is no polynomial time quantum algorithm that approximates lattice problems within polynomial factors.**
>
>---

>[!remark] Remark on Lattice-Based Cryptography ([[../../../../../PDFs/sabani2024.pdf#page=11|Source]])
>Lattice-based cryptographic offer many advantages over **factorization** and **discrete logarithm** problems (which both can be solved in polynomial time with quantum computing, i.e. Shore's algorithm)
>- efficient and parallelizable
>- operations are simple, i.e. linear vector and matrix operations with small moduli
>- fully homomorphic encryption can be achieved