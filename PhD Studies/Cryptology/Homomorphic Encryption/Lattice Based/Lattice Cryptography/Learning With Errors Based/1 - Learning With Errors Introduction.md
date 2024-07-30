>[!def] Definition Learning from Parity with Error/Noise (LPN) 
>Let $n \geq 1$ and $0<\varepsilon< \frac{1}{2}$, find an unknown $\mathbf{s} \in \mathbb{Z}_{2}^n$ such that the list of equations with errors
>$$\begin{align}
> \left\langle \mathbf{s}\,,\,\mathbf{a}_{1} \right\rangle &\approx_{\varepsilon} b_{1} \;\;(\text{mod } 2) \\
> \left\langle \mathbf{s}\,,\,\mathbf{a}_{2} \right\rangle &\approx_{\varepsilon} b_{2} \;\;(\text{mod } 2) \\
> &\vdots
>\end{align}$$
>where the $\mathbf{a}_{i}$s are chosen independently from the uniform distribution on $\mathbb{Z}_{2}^n$ and each equation is correct independently with probability $1-\varepsilon$
>
>>[!remark]- Remark on the Term Parity
>>Parity is a function on the bitstream of a string $s = (0+1)^n$ of the following form
>>$$\text{parity}(s)=\begin{cases}
>>0 & \text{ if number of } 1\text{'s is even} \\
>>1 & \text{ if number of }1\text{'s is odd}
>>\end{cases}$$
>
>>[!remark]- Remark on Hardness of the Problem
>>There is no algorithm which solves this problem in $\text{poly}(n)$ time even for small $\varepsilon$.
>
>>[!example]- Algorithmic Example (Useful)
>>1. Let $\mathbf{s} \in \mathbb{Z}_{2}^n$ be a randomly chosen secret by Alice. 
>>2. A request algorithm is introduced:
>>	1. Alice chooses some $\mathbf{a} \in \mathbb{Z}_{2}^n$
>>	2. Alice generates a noisy parity response $$b=\left\langle \mathbf{s}\,,\, \mathbf{a} \right\rangle + \begin{cases}
>> 0 &\text{with probability } 1-\varepsilon \\
>> 1 &\text{with probability } \varepsilon
>> \end{cases}$$
>> 	where $\varepsilon$ represents the noise or error
>> 	1. Alice sends $\mathbf{a}$ and $b$ to Bob
>>3. Bob's goal is to determine the secret vector $\mathbf{s}$ by querying Alice multiple times using the request algorithm. Each query provides a new pair $(\mathbf{a},b)$.

>[!remark]- Remark on LWE as an Extension of LPN
> Instead of choosing the modulus $n=2$ in LPN, the modulus is chosen $n>2$ in LWE.


>[!def] Definition Learning with Errors (LWE) ([[../../../../../../PDFs/gentry2013.pdf#page=8|Source]])
>For security parameter $\lambda$, let 
>- $n=n(\lambda)$ be an integer dimension
>- $q=q(\lambda)\leq 2$ be an integer
>- $\chi=\chi(\lambda)$ be a distribution over $\mathbb{Z}$
>
>The **LWE$_{n,q,\chi}$** problem *is to distinguish* the following two distributions:
>1. One samples $(\mathbf{a}_{i}, b_{i})$ uniformly from $\mathbb{Z}_{q}^{n+1}$, i.e. $\mathbf{a}_{i} \in \mathbb{Z}_{q}^n$ and $b_{i} \in \mathbb{Z}_{q}$
>2. One first draws $\mathbf{s} \leftarrow \mathbb{Z}^n_{q}$ uniformly and then samples $(\mathbf{a}_{i}, b_{i}) \in \mathbb{Z}^{n+1}_{q}$, i.e. $\mathbf{a}_{i} \in \mathbb{Z}_{q}^n$ and $b_{i} \in \mathbb{Z}_{q}$, by 
>	- sampling $\mathbf{a}_{i} \leftarrow \mathbb{Z}_{q}^n$ uniformly
>	- $e_{i} \leftarrow \chi$
>	- setting $b_{i} = \left\langle \mathbf{a}_{i}\,,\, \mathbf{s} \right\rangle + e_{i}$
>
>The LWE$_{n,q,\chi}$ assumption is that the LWE$_{n,q,\chi}$ problem is infeasible.

>[!remark]
>>[!remark]- Remark on LWE Generally ([[../../../../../../PDFs/sabani2024.pdf#page=13|Source]])
>> The LWE problem asks to solve the discrete linear equation
>> $$\mathbf{b} =\mathbf{A}\mathbf{s}+ \mathbf{e} \text{ mod }q$$
>> given $(\mathbf{A},\mathbf{b})$ and finding the secret vector $\mathbf{s}$. The entries $e_{i} \in \mathbf{e}$ denote the discrete rounding error, such that
>> $$\begin{align}
>> \left\langle \mathbf{a}_{i}\,,\, \mathbf{s} \right\rangle \approx_{e_{i}} b_{i}
>>\end{align}$$ 
>
>>[!remark]- Remark on Security of LWE ([[../../../../../../PDFs/sabani2024.pdf#page=14|Source]])
>>The security of LWE is based on the hardness of **shortest integer problem (SIP)** for [[../Lattice Based/Lattice Cryptography/Elementary Definitions|lattices]].
>
>>[!remark]- Remark on Error $\mathbf{e}=\mathbf{0}$ ([[../../../../../../PDFs/regev2024.pdf#page=2|Source]])
>>If we consider $\mathbf{e}=\mathbf{0}$, then the problem collapses to the simple linear equation which can be solved by Gaussian elimination and can be solved for $\mathcal{O}(n)$ equations in $\text{poly}(n)$ time.
>>
>>Given $\mathbf{e}\neq \mathbf{0}$ the problem becomes untractable

>[!def] Definition Real Modulus ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
>Let $x,y \in \mathbb{R}^+$
>$$x \text{ mod } y := x - \left\lfloor  \frac{x}{y}  \right\rfloor y $$
>
>>[!example]-
>>Let $$\begin{align}
>> x &= 5.3 \\
>> y &= 1 
>>\end{align}$$ Then
>>$$\begin{align}
>> 5.3 \text{ mod } 1 &= 5.3 - \left\lfloor  \frac{5.3}{1}  \right\rfloor 1 \\
>> &= 5.3-5 \\
>> &= 0.3
>>\end{align}$$

^969363

>[!def] Definition Closest Integer ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
> Let $x \in \mathbb{R}$, the closest integer to $x$ is defined as
> $$\lfloor  x  \rceil \in \mathbb{Z} $$

>[!def] Definition Cyclic Group $\mathbb{Z}_{p}$ ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
> The cyclic group $\mathbb{Z}_{p}$ with $p \in\mathbb{Z}$ over addition is given as
> $$\mathbb{Z}_{p} = \{ 0,1,\dots,p-1 \}$$

>[!def] Definition Negligible Functions ([[../../../../../../PDFs/regev2024.pdf#page=12|Source]])
>Let $n$ be some number. A function $f$ is called *negligible* if for any constant $c>0$
>$$\lim_{ n \to \infty } n^cf(n)=0 \qquad $$

>[!def] Definition Gaussian Function ([[../../../../../../PDFs/regev2024.pdf#page=13|Source]])
>Let $\mathbf{x} \in \mathbb{R}$ and the scaling factor $s>0$, the Gaussian function is given by
>$$\rho_{s}(\mathbf{x}):= \exp\left( -\pi \left\lvert \left\lvert  \frac{\mathbf{x}}{s}  \right\rvert \right\rvert^2   \right)$$
>
>>[!remark]
>>The normal distribution with mean $\mu=0$ and variance $\sigma^2$ as distribution on $\mathbb{R}$ is given by the density function
>>$$\frac{1}{\sqrt{ 2\pi }\sigma}\exp\left( -\frac{1}{2}\left( \frac{x}{\sigma} \right)^2 \right)$$ 

^cd948a

>[!def] Definition Probability Density Function based on the Gaussian Function ([[../../../../../../PDFs/regev2024.pdf#page=13|Source]])
>For
>$$\int _{\mathbf{x}\in\mathbb{R}^n}\rho_{s}(\mathbf{x}) \, dx = s^n$$
>The $n$-dimensional Probability Density Function (PDF) is given by
>$$\nu_{s}:= \frac{\rho_{s}}{s^n}$$

>[!def] Definition Lattice Smoothed Gaussian ([[../../../../../../PDFs/regev2024.pdf#page=17|Source]])
>Let $L$ be an $n$-dimensional lattice and $\epsilon>0$. The smoothing parameter $n_{\epsilon}(L)$ with respect to lattice $L$ is the smallest $s$ such that
>$$\rho_{1/s}(L^*\setminus \{ \mathbf{0} \})\leq \epsilon$$
>
>>[!remark]
>> $p_{1/s}$ is a continuous and strictly decreasing function of $s$ and
>>  $$\begin{align}
>> \lim_{ s \to 0 } \rho_{1/s}(L^*\setminus \{ \mathbf{0} \})  &= \infty\\
>> \lim_{ s \to \infty } \rho_{1/s}(L^*\setminus \{ \mathbf{0} \})  &= 0\\
>>\end{align}$$

>[!def] Definition Discrete Gaussian Probability Distribution ([[../../../../../../PDFs/regev2024.pdf#page=14|Source]])
>Let $A$ be a countable set and $s>0$. The discrete Gaussian probability distribution $D_{A,s}$ is defined as
>$$\forall \mathbf{x} \in A, D_{A,s}(\mathbf{x}):= \frac{\rho_{s}(\mathbf{x})}{\rho_{s}(A)}$$
>where $\rho_{s}$ is the [[#^cd948a|Gaussian function]]
>>[!pic] Illustration ([[../../../../../../PDFs/regev2024.pdf#page=7|Source]])
>> ![[../../Figures/discrete_gaussian.png]]
>> where $s$ denotes the width of the distribution.

>[!def] Definition Torus Quotient Group
>Let $\mathbb{T}=\mathbb{R} / \mathbb{Z}$ be the quotient group defined for the [[#^969363| real modulus]] with modulus $y=1$.
>
>The Torus can also be given in interval representation $$\mathbb{T}= [0,1)$$
>
>>[!remark]-
>> Any $x_{1},x_{2} \in \mathbb{T}$ are equivalent if and only if there exists some $a \in \mathbb{Z}$, such that $$x_{1} -a = x_{2}$$
>> or equivalently 
>> $$x_{1} \equiv x_{2} \;\;(\text{mod } 1)$$

>[!def] Definition Periodic Normal Distribution ([[../../../../../../PDFs/regev2024.pdf#page=14|Source]])
>Let $\beta \in \mathbb{R}^+$. The periodic normal distribution $\Psi_{\beta}$ is a normal distribution with zero mean $\mu=0$ and standard deviation $\sigma=\frac{\beta}{\sqrt{ 2\pi }}$ reduced by modulo $1$. This distribution is defined on the torus $\mathbb{T}$ for all $r \in [0,1)$ with $$\Psi_{\beta}(r) := \sum_{k=-\infty}^\infty \frac{1}{\beta}\exp\left( -\pi\left( \frac{r-k}{\beta} \right)^2 \right)$$
>>[!Observation]- Literature and Quotes on Circular Normal Distributions
>>- [[../../../../../../PDFs/jammalamadaka2001.pdf#page=48|Topics in Circular Statistics - 2.2.4 Circular Normal Distribution (Page 35)]]
>>---
>>Quote
>>>This distribution was introduced as a statistical model by von Mises (1918) and was discussed earlier by Langevin (1905), in the context of physics. Gumbel et al. (1953), who provide a nice discussion of this distribution and some of its properties, call it a "Circular Normal distribution" to emphasize its importance and similarities to the Normal distribution on the real line.
>>>
>>>The CN distribution has been extensively studied and inference techniques well developed. Therefore this is the model of choice for circular data in most applied problems.
>>
>>---
>>- [[../../../../../../PDFs/kurz2014.pdf|Efficient Evaluation of the Probability Density Function of a Wrapped Normal Distribution]]
>>
>>---
>>Quote
>>>[...] evaluation of the WN probability density function can appear difficult because it involves an infinite series
>>
>>---

^ab0e75

>[!lemma] Lemma Bootstrapping ([[../../../../../../PDFs/regev2024.pdf#page=19|Source]])
>There exists an efficient algorithm that, given any $n$-dimensional lattice $L$ and $r > 2^{2n}\lambda_{n}(L)$, outputs a sample from a distribution that is within statistical distance $2^{-\Omega(n)}$ of $D_{L,r}$.
>
>>[!proof] Proof see paper
>
>>[!remark]- Remark
>> - This lemma ensures us, that the errors we produce for our LWE problem are always statistically close to our lattice vector. The higher the dimensionality of the lattice $L$ is, the more likely the error is close to the lattice vector
>>

>[!lemma] Theorem on Security ([[../../../../../../PDFs/regev2024.pdf#page=3|Source]])
> If there exists an efficient algorithm that solves $\text{LWE}_{p, \Psi_{\alpha}}$ with $\alpha \in (0,1)$ and $n,p \in \mathbb{Z}$ and $\alpha p>2\sqrt{ n }$, then there exists an efficient quantum algorithm that approximates the  [[../2 - Computational Problems#^02fc56|decision version of the shortest vector problem]] ($\text{GAPSVP}$) and the shortest independent vectors problem $\text{SIVP}$ to within $\widehat{\mathcal{O}}\left( \frac{n}{\alpha} \right)$ in the worst case. 
>
