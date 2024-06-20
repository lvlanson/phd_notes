>[!def] Definition Shortest Vector Problem (SVP) ([[../../../../../PDFs/sabani2024.pdf#page=6|Source]])
>
>Given a basis $\mathbf{B}=\{\mathbf{b}_{1}, \mathbf{b}_{2},\dots,\mathbf{b}_{n}  \}$ of a lattice $\mathcal{L}(\mathbf{B})$, find the nonzero shortest vector $\mathbf{v}$, i.e., find $\mathbf{v} \in \mathcal{L}$ for which $$\lvert\lvert \mathbf{v} \rvert\rvert = \lambda_{1}(\mathcal{L}) $$
>where $\lambda_{1}$ denotes the [[1 - Elementary Definitions#^5efb92|minimum distance of a lattice]].
>>[!pic] Illustration
>>![[../Figures/shortes_vector_problem.png|center| 450]]
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
>>[!pic]- Illustration
>>![[../Figures/gapsvp.png|center|300]]
>>The gap is given by the area between the two circle. Given some $d$ outside the outer circle, NO is given by the instance, given some $d$ inside the inner circle, YES is given by the instance. The area inbetween won't give a response.