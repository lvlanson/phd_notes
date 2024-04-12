>[!def] Definition Scalar Product
> Let $\mathcal{H}$ be a vector space over $\mathbb{K}\in\{ \mathbb{R}, \mathbb{C} \}$. A mapping $\left\langle \, . \,,\,.\, \right\rangle$ is called a **scalar product**, if it has the following properties, $\forall x,y,z \in H$ and $\lambda \in \mathbb{K}$:
> $$\begin{alignat}{2}
> (i)\quad & \langle x\,,\,x \rangle\geq 0  \\
>      &\langle x \,,\,x \rangle = 0 \Longleftrightarrow x = 0 \\
> (ii)\quad & \langle x\,,\,y \rangle = \overline{\langle y\,,\,x \rangle} \\
> (iii)\quad& \left\langle \lambda x\,,\,y \right\rangle = \lambda \left\langle x\,,\,y \right\rangle \\
>  & \left\langle x+z\,,\,y \right\rangle = \left\langle x\,,\,y \right\rangle + \left\langle z\,,\,y \right\rangle 
>\end{alignat}$$
>>[!remark]-
>>It follows without proof
>>$$\begin{align}
>> \left\langle x\,,\,\lambda y \right\rangle &= \overline{\lambda} \left\langle x\,,\,y \right\rangle  \\
>> \left\langle x\,,\,y+z \right\rangle &= \left\langle x\,,\,y \right\rangle + \left\langle x\,,\,z \right\rangle  
>>\end{align}$$

>[!def] Definition Pre-Hilbert Space
>A normed space is called a **pre-Hilbert space**, if there exists a scalar product on $\mathcal{H}$ such that
>$$\lvert\lvert x \rvert\rvert_{\mathcal{H}} = \sqrt{ \left\langle x\,,\,x \right\rangle  } $$
>defines a norm on $\mathcal{H}$

>[!def] Definition Hilbert Space
>A **pre-Hilbert space** $\mathcal{H}$ is called **Hilbert space**, if $\mathcal{H}$ is complete with respect to $\lvert\lvert\, . \rvert\rvert_{\mathcal{H}}$

>[!property] Property Cauchy-Schwarz Inequality
>Let $\mathcal{H}$ be a **pre-Hilbert space** equipped with a scalar product $\left\langle \, . \,,\,. \, \right\rangle$. Then it holds the **Cauchy-Schwarz** inequality
>$$\lvert \left\langle x\,,\,y \right\rangle  \rvert \leq \lvert\lvert x \rvert\rvert _{\mathcal{H}} \cdot \lvert\lvert y \rvert\rvert_{\mathcal{H}} \tag*{$\forall x,y \in \mathcal{H}$}$$
>>[!note]
>>Equality holds if $x$ and $y$ are linearly dependent

^3fd445

>[!property] Property Parallelogramequation / Polarization Identity
>Let $\mathcal{H}$ be a normed vector space with $\lvert\lvert \,. \rvert\rvert$, then $\mathcal{H}$ is a **pre-Hilbert space** if and only if the **parallelogramequation** holds: $\forall x,y \in \mathcal{H}$
>$$\lvert\lvert x+y \rvert\rvert^2 + \lvert\lvert x-y \rvert\rvert^2 = 2\big(\lvert\lvert x \rvert\rvert^2 + \lvert\lvert y \rvert\rvert^2  \big)  $$
>with the corresponding scalar product being defined as
>$$\left\langle x\,,\,y \right\rangle = \begin{cases}
> \frac{1}{4}\big(\lvert\lvert x+y \rvert\rvert ^2 - \lvert\lvert x-y \rvert\rvert^2 \big) & \text{ if } \mathbb{K} = \mathbb{R} \\
> \frac{1}{4} \big(\lvert\lvert x+y \rvert\rvert ^2 - \lvert\lvert x-y \rvert\rvert^2 \big) + \frac{i}{4}\big(\lvert\lvert x+iy \rvert\rvert^2 - \lvert\lvert x-iy \rvert\rvert^2  \big) &\text{ if } \mathbb{K} = \mathbb{C}
>\end{cases}$$

^d69824

>[!property] Corollary
>Let $\mathcal{H}$ be a **pre-Hilbert** space. Then we have the following assertions
>1. Let $\{ x_{j} \}_{j}, \{ y_{j} \}_{j} \subset H$ with $x,y \in \mathcal{H}$ and
>$$\begin{align}
> \lim_{ j \to \infty } x_{j} &= x \\
> \lim_{ j \to \infty } y_{j} &= y
>\end{align}$$
>Then it holds
>$$\lim_{ j \to \infty } \left\langle x_{j}\,,\,y_{j} \right\rangle = \left\langle x\,,\,y \right\rangle $$
>
>>[!proof]-
>>First note, by the claim that the identity holds, we can assert
>>$$\begin{align}
>> \lim_{ j \to \infty } \lvert \left\langle x_{j}\,,\,y_{j} \right\rangle - \left\langle x\,,\,y \right\rangle  \rvert  &= 0
>>\end{align}$$
>>We show the assertion by using the [[#^3fd445| Cauchy Schwarz inequality]] on the sequential term. Once we have shown that the identity holds, it follows that the given corollary holds. We get
>>$$\begin{align}
>> \lvert \left\langle x_{j}\,,\,y_{j} \right\rangle - \left\langle x\,,\,y \right\rangle   \rvert &= \lvert \left\langle x_{j}\,,\,y_{j} \right\rangle + \underbrace{ \left\langle x\,,\,y_{j} \right\rangle-\left\langle x\,,\,y_{j} \right\rangle }_{ =0 } - \left\langle x\,,\,y \right\rangle    \rvert  \\
>> &= \lvert \left\langle x-x_{j}\,,\,y_{j} \right\rangle + \left\langle x\,,\, y-y_{j} \right\rangle  \rvert \tag{IP Linearity} \\
>> &\leq \lvert \left\langle x-x_{j}\,,\,y_{j} \right\rangle \rvert  + \lvert \left\langle x\,,\,y-y_{j} \right\rangle \rvert \tag{Triangle Inequality} \\
>> &\leq \underbrace{ \lvert\lvert x - x_{j} \rvert\rvert_{\mathcal{H}} }_{ \underset{l \to \infty}\to 0 } \cdot \lvert\lvert y_{j} \rvert\rvert_{\mathcal{H}} + \lvert\lvert x \rvert\rvert_{\mathcal{H}} \cdot \underbrace{ \lvert\lvert  y-y_{j} \rvert\rvert_{\mathcal{H}} }_{  \underset{l \to \infty}\to 0  }   \\
>> & \underset{l \to \infty}\to 0  \tag*{$\square$}
>>\end{align}$$
>
>2. For $x = \sum\limits_{n \in \mathbb{N}} x_{n} \in \mathcal{H}$ it holds $\forall y \in H$:
>$$\begin{align}
> \left\langle x\,,\,y \right\rangle &= \left\langle \sum_{n \in \mathbb{N}}x_{n}\,,\, y\right\rangle  \\
> &= \sum_{n \in \mathbb{N}} \left\langle x_{n}\,,\,y \right\rangle 
>\end{align} $$
>
>>[!proof]-
>>We use the identity $$x = \sum\limits_{n \in \mathbb{N}} x_{n}$$ and the properties of the scalar product and the result of the previous corollary (1).
>>$$\begin{align}
>> \left\langle x\,,\,y \right\rangle &= \left\langle  \sum_{n=1}^\infty x_{n}\,,\,y \right\rangle  \\
>> &= \left\langle \lim_{ j \to \infty } \sum_{n=1}^j x_{n}\,,\,y \right\rangle \\
>> &= \lim_{ j \to \infty } \left\langle \sum_{n=1}^jx_{n}\,,\,y  \} \right\rangle \tag{Previous Corollary}\\
>> &= \lim_{ j \to \infty } \sum_{n=1}^j \left\langle x_{n}\,,\,y \right\rangle  \tag{IP Linearity}\\
>> &= \sum_{n=1}^\infty \left\langle x_{n}\,,\,y \right\rangle    \tag*{$\square$}
>>\end{align}$$
>
>3. Let $U \subset \mathcal{H}$ be a **dense** subspace of $\mathcal{H}$. We have
>	$$\forall u \in U, x \in \mathcal{H}: \; \left\langle u\,,\,x \right\rangle =0 \implies x = 0$$
>	
>>[!proof]-
>>>[!recall]- Recall Dense Subsets
>>> If a set $U \in \Omega$ is dense in $\Omega$, then for any $\omega \in \Omega$ there exists a sequence in $\{ u_{j} \}_{j} \subset U$ such that $\lim_{ j \to \infty } u_{j} = x$. Speaking, there exists a sequence in $U$ which can approximate any $\omega \in \Omega$ arbitrarily well. 
>>
>>Let $x \in \mathcal{H}$, since $U$ is dense in $\mathcal{H}$, there exists a sequence $\{ u_{j} \}\subset U$ with $\lim\limits_{ _j \to \infty }u_{j} = x$. Hence, we have by the corollary
>>$$\begin{align}
>> \underbrace{ \left\langle u_{j}\,,\, x\right\rangle }_{ =0 } \underset{j \to \infty}\to \left\langle x\,,\,x \right\rangle  = \lvert\lvert x \rvert\rvert _{H}^2 = 0 \iff x=0
>>\end{align}$$
>

>[!def] Definition Orthogonality 
>Let $\mathcal{H}$ be a **pre-Hilbert** space
>1. $x,y \in \mathcal{H}$ are **orthogonal**, if $$\left\langle x\,,\,y \right\rangle=0$$ We denote orthogonality by $$x \perp y : \iff\left\langle x\,,\,y \right\rangle=0$$
>2. Two subspaces $U,V \subset \mathcal{H}$ are orthogonal if $$\forall u \in U \text{ and }\forall v \in V: \left\langle u\,,\,v \right\rangle = 0$$ 
>3. Let $U \subset \mathcal{H}$ be a subspace. Then we call $$U^\perp = \{  v \in \mathcal{H}: \, v \perp u\;\; \forall u \in U \}$$
>>[!remark]
>>$$U \cap U^\perp = \{  0 \}$$
>>Because
>>$$x \in (U \cap U^\perp) \implies \left\langle x\,,\,x \right\rangle = 0 = \lvert\lvert x \rvert\rvert _{\mathcal{H}}^2 \iff x = 0$$
>

>[!property] Properties on Orthogonality 
>1. $x,y \in \mathcal{H}$ with $x \perp y \; \implies \; \lvert\lvert x+y \rvert\rvert^2_{\mathcal{H}} = \lvert\lvert x \rvert\rvert_{\mathcal{H}}^2 + \lvert\lvert y \rvert\rvert^2_{\mathcal{H}}$
>
>>[!proof]-
>>$$\begin{align}
>> \lvert\lvert x+y \rvert\rvert^2_{\mathcal{H}} &= \left\langle x+y\,,\,x+y \right\rangle  \\
>> &= \left\langle x\,,\,x \right\rangle + \underbrace{ \left\langle x\,,\,y \right\rangle }_{ =0 } + \underbrace{ \left\langle y\,,\,x \right\rangle }_{ =0 } + \left\langle y\,,\,y \right\rangle \tag{IP Linearity} \\
>> &= \lvert\lvert x \rvert\rvert^2_{\mathcal{H}} + \lvert\lvert y \rvert\rvert_{\mathcal{H}}^2 \tag{Orthogonality} 
>>\end{align} $$
>>$$\tag*{$\square$}$$
>
>>[!note] Note $\lvert\lvert x+y \rvert\rvert^2$ represents the hypotenuse from the Pythagorean theorem
>
>2. The following assertion holds $$U \subset \mathcal{H} \; \implies \; U^\perp \text{ is closed in } \mathcal{H} \text{ and } (\overline{U})^\perp = U^\perp $$
>
>>[!proof]-
>>(i) 
>>First, we show $U^\perp$ is a closed linear subspace. Let $y_{1},y_{2}\in U^\perp$, $\lambda, \mu \in \mathbb{K}$ and $x \in U$:
>>$$\begin{align}
>> \left\langle \lambda y_{1} +\mu y_{2} \,,\, x  \right\rangle &= \lambda \underbrace{ \left\langle y_{1}\,,\,x \right\rangle }_{ =0 } + \mu \underbrace{ \left\langle y_{2}\,,\,x \right\rangle   }_{ =0 } \\
>> &= 0 \tag{Orthogonality}
>>\end{align}$$
>>Since $\lambda y_{1} + \mu y_{2} \in U^\perp$ we can deduce $U^\perp$ is a **linear subspace**. Further $U^\perp \neq \emptyset$ because $U^\perp \cap U = \{ 0 \}$
>>
>>(ii) 
>>We now show that $U^\perp$ is closed. Let $\{ y_{j} \}_{j} \subset U^\perp$ with $y_{j}  \underset{j \to \infty}\to y \in \mathcal{H}$. We want to show that $y \in U^\perp$. Therefore, let $x \in U$:
>>$$\begin{align}
>> \left\langle x\,,\,y \right\rangle &= \lim_{ j \to \infty } \underbrace{ \left\langle x\,,\,y_{j} \right\rangle }_{ =0 } \\
>> &= 0  \\
>> &\implies y \in U^\perp \\
>> &\implies U^\perp \text{ is a closed subspace}
>>\end{align}$$
>>>[!recall]- Recall Closed Subspace
>>> A subspace is closed if it contains all limit points of any converging sequence.
>>
>>(iii)
>>To show that $(\overline{U})^\perp = U^\perp$ we first show $(\overline{U})^\perp \subseteq U^\perp$. Therefore, let $v \in (\overline{U})^\perp$
>>$$\begin{align}
>> \forall u \in \overline{U}: &\left\langle v\,,\,u \right\rangle = 0  \\
>> \forall u \in U: &\left\langle v\,,\,u \right\rangle = 0 \tag{$U \subset \overline{U}$} \\
>>\, \tag*{$\checkmark$}
>>\end{align}$$
>>Now we show that $U^\perp \subseteq  (\overline{U})^\perp$. Let 
>>$$v \in U^\perp, u \in\overline{U} \; \implies \; \exists \{ u_{j} \}_{j=1}^\infty \in U \text{ with } \lim_{ j \to \infty } u_{j} = u$$
>>This result is justified by the density of $U \in \overline{U}$. We continue
>>$$\begin{align}
>> \left\langle v\,,\,u \right\rangle &=\left\langle v\,,\,\lim_{ j \to \infty } u_{j} \right\rangle \\
>> &= \lim_{ j \to \infty } \underbrace{ \left\langle v \,,\,u_{j} \right\rangle }_{ =0 } \\
>> &= 0 
>>\end{align}$$
>> Since $u \in \overline{U}$ and $\left\langle u\,,\,v \right\rangle \implies v \in (\overline{U})^\perp$
>> $$\tag*{$\checkmark$}$$
>> Hence,
>> $$\implies (\overline{U})^\perp \subseteq U^\perp \land U^\perp \subseteq(\overline{U})^\perp \implies (\overline{U})^\perp = U^\perp$$
>
>3. In general it golds $U \subset \left(U^\perp\right)^\perp$
>
>>[!proof]-
>>$$\begin{align}
>> u \in U, v \in U^\perp \implies \left\langle u\,,\,v \right\rangle = 0 \implies u \in (U^\perp)^\perp 
>>\end{align}$$
>>>[!note]
>>>Since $v \in U^\perp$ and $u \perp v \implies u \in (U^\perp)^\perp$  