>[!remark] Motivation
>>[!recall] Recall [[../../Linear Algebra/Inner Product/Orthogonal Projection|Orthogonal Projection]]
> 
>We want to investigate if for some arbitrary $f \in \mathcal{H}$ we can find in $U \in \mathcal{H}$ some $g_{0} \in U$ such that
>$$\lvert\lvert f-g_{0} \rvert\rvert = \underset{g \in U}{\text{inf}} \; \lvert\lvert f-g \rvert\rvert $$
>which minimizes the distance between $f$ and $U$, which we will refer to the best approximation $g_0 \in U$. The figure below illustrates the objective we are describing.
>![[Figures/Approximation_Motivation.png|center|400]]
>>[!question] Questions
>>1. When does such an element $g_{0}$ exist?
>>2. If it exists, is $g_0$ unique?

>[!def] Definition Best Approximation
>Denote the minimal distance
>$$\delta(f,U) = \underset{g \in U}{\text{inf}}\; \lvert\lvert f -g \rvert\rvert$$
>If there exists some $g_{0} \in U$ with $\delta(f,U)= \lvert\lvert f - g_{0} \rvert\rvert$ then we call $g_{0}$ **best approximation** of $f$ in $U$ 

>[!def] Definition Convexity
>Let $U \subset \mathcal{H}$. $U$ is convex if $\forall x_{1},x_{2} \in U$ and $\forall \lambda \in [0,1]$ it holds
>$$\lambda x_{1}+(1-\lambda)x_{2} \in U$$
>>[!Remark]
>>Any linear subspace is convex.

>[!theorem] Orthogonal Projection Theorem / Hilbert Projection Theorem
>Let $\mathcal{H}$ be a Hilbert space and let $U\neq \emptyset$ convex and closed with $U \subseteq \mathcal{H}$. Then there exists for any $f \in \mathcal{H}$ a uniquely determined best approximation $g_{0} \in U$.
>
>Moreover, the mapping
>$$\begin{align}
> P:&H \to U \\
> P:&f \mapsto g_{0}
>\end{align}$$
>is continuous
>>[!proof]-
>>1. Uniqueness
>>
>>>The strategy for this proof is to construct a contradiction. We assume to have 2 best approximations, and construct by our convexity property another best approximation. We will enforce a contradiction and show, that the constructed best approximation is less than the best approximation by definition. Therefore, there only can be one single best approximation. 
>>>
>>>Assume, there exist $g_{1},g_{2} \in U$ with $g_{1}\neq g_{2}$ which are both best approximation of $f \in U$. Then according to convexity with $\lambda = \frac{1}{2}$ we get
>>> $$g = \frac{g_{1}+g_{2}}{2} \in U$$
>>> We now perform an investigation if $g$ is also a best approximation. We have
>>> $$\begin{align}
>>>\delta(f,U) &= \underset{h\in U}{\text{inf}}\;\lvert\lvert f-h \rvert\rvert_{\mathcal{H}} \\
>>> &\leq \lvert\lvert f-g \rvert\rvert _{\mathcal{H}} \tag{$g$ can also be worse} \\
>>> &=\left\lvert \left\lvert  f- \frac{g_{1}+g_{2}}{2}  \right\rvert \right\rvert _{\mathcal{H}}  \tag{construction}\\
>>> &= \left\lvert \left\lvert  \frac{2f}{2}- \frac{g_{1}+g_{2}}{2}  \right\rvert \right\rvert _{\mathcal{H}} \\
>>> &= \left\lvert \left\lvert  \frac{2f - g_{1}+g_{2}}{2}  \right\rvert \right\rvert _{\mathcal{H}} \\
>>> &= \left\lvert \left\lvert  \frac{f - g_{1}}{2} + \frac{f-g_{2}}{2}  \right\rvert \right\rvert _{\mathcal{H}} \\
>>> &= \frac{1}{2}\left\lvert \left\lvert  f - g_{1} + f-g_{2}  \right\rvert \right\rvert _{\mathcal{H}} \\
>>> &\leq \frac{1}{2}\underbrace{ \left\lvert \left\lvert  f - g_{1} \right\rvert \right\rvert_{\mathcal{H}} }_{ =\delta(f,U) } + \underbrace{ \left\lvert \left\lvert f-g_{2}  \right\rvert \right\rvert _{\mathcal{H}} }_{ =\delta(f,U) } \tag{ Triangle Inequality}\\
>>> &= \frac{1}{2}\delta(f,U) + \frac{1}{2}\delta(f,U) \\
>>> &= \delta(f,U)
>>>\end{align}$$
>>>We can conclude that $g$ is also a best approximation of $f$ in $U$ because $\delta(f,U)=\lvert\lvert f-g \rvert\rvert_{\mathcal{H}}$.
>>>
>>>Recall $g_1 \neq g_2$, hence
>>>$$\lvert\lvert g_{1}-g_{2} \rvert\rvert_{H} >0 $$
>>>We now use the [[B1 - Hilbert Spaces#^d69824|parallelolgram-equation]] and obtain
>>>$$\begin{align}
>>> \lvert\lvert f-g \rvert\rvert ^2_{\mathcal{H}} &= \left\lvert \left\lvert  \frac{2f}{f} - \frac{g_{1}+g_{2}}{2}  \right\rvert \right\rvert_{\mathcal{H}}^2 \\
>>> &= \frac{1}{4} \lvert\lvert f-g_{1}+f-g_{2} \rvert\rvert^2_{\mathcal{H}}   \\
>>> &= \frac{1}{4}\Big(2 \underbrace{ \lvert\lvert  f-g_{1} \rvert\rvert^2_{\mathcal{H}} }_{ =\delta(f,U) } + 2\underbrace{ \lvert\lvert f-g_{2} \rvert\rvert_{\mathcal{H}}^2 }_{ =\delta(f,U) } - \underbrace{ \lvert\lvert g_{1}-g_{2} \rvert\rvert_{\mathcal{H}}^2 }_{ >0 }   \Big) \tag{ Parallelogram-Equation} \\
>>> &= \frac{1}{4}\Big(2\delta(f,U)+2\delta(f,U) - \lvert\lvert g_{1}-g_{2} \rvert\rvert_{\mathcal{H}}^2\Big) \\
>>> &= \delta(f,U) - \frac{1}{4}\lvert\lvert g_{1}-g_{2} \rvert\rvert_{\mathcal{H}}^2 \\
>>> &< \delta(f,U)
>>>\end{align}$$
>>>This is a contradiction. We claimed that $g$ is the best contradiction, but it is smaller than what we defined as best contradiction, therefore there can't be two different best approximations.
>>>$$\tag*{$\checkmark$}$$
>>
>>2. Existence
>>
>>> Denote $\alpha = \delta(f,U)$, therefor we can also write $\alpha^2 = \delta(f,U)^2 = \underset{g \in U}{\text{inf}}\; \lvert\lvert f-g \rvert\rvert^2$. Now, we assert $\forall \varepsilon>0$ and some $g_{\varepsilon} \in U$ (dependent on the choice of $\varepsilon$) the following statement holds true
>>> $$\alpha^2 \leq \lvert\lvert f - u_{\varepsilon} \rvert\rvert^2_{\mathcal{H}} < \alpha^2 + \varepsilon $$
>>> Note, equality for the left side holds, if the best approximation is $u_{\varepsilon}$.  We choose
>>> $$\varepsilon = \frac{1}{n} \quad n \in \mathbb{N}^+$$
>>> Further, we can find a sequence $\{ u_{n} \}_{n=1}^\infty \subseteq U$ such that
>>> $$\begin{alignat}{2}
>>> \alpha^2 &\leq \lvert\lvert f - u_{n} \rvert\rvert^2_{\mathcal{H}} < \alpha^2 + \frac{1}{n}  \qquad&&\Big\vert -\alpha^2 \\
>>> 0 &\leq \lvert\lvert  f-u_{n} \rvert\rvert^2_{\mathcal{H}} - \alpha^2 < \frac{1}{n} \tag{1}
>>>\end{alignat}$$
>>>We can construct another sequence with the same assertions for some index $m \in \mathbb{N}^+$, hence
>>> $$0 \leq \lvert\lvert  f-u_{m} \rvert\rvert^2_{\mathcal{H}} - \alpha^2 < \frac{1}{m} \tag{2}$$
>>> Adding the relations $(1)$ and $(2)$ gives
>>> $$\begin{alignat}{2}
>>> 0 &\leq \lvert\lvert  f-u_{n} \rvert\rvert^2_{\mathcal{H}} + \lvert\lvert  f-u_{m} \rvert\rvert^2_{\mathcal{H}} - 2\alpha^2 < \frac{1}{n} + \frac{1}{m} \qquad&&\Big\vert \cdot2 \\
>>> 0 &\leq \underbrace{ 2\lvert\lvert  f-u_{n} \rvert\rvert^2_{\mathcal{H}} + 2\lvert\lvert  f-u_{m} \rvert\rvert^2_{\mathcal{H}} }_{ \text{Parallelogram-Equation} } - 4\alpha^2 < \frac{2}{n} + \frac{2}{m} \tag{3}
>>>\end{alignat}$$
>>>Note, we can identify the [[B1 - Hilbert Spaces#^d69824|parallelogram-equation]], i.e.
>>>$$\begin{align}
>>> 2\lvert\lvert  f-u_{n} \rvert\rvert^2 + 2\lvert\lvert_{\mathcal{H}}  f-u_{m} \rvert\rvert^2_{\mathcal{H}} &= 2\big(\lvert\lvert  f-u_{n} \rvert\rvert^2_{\mathcal{H}} + \lvert\lvert  f-u_{m} \rvert\rvert^2_{\mathcal{H}}\big) \\
>>> &= \lvert\lvert (f-u_{n}) + (f-u_{m})\rvert\rvert^2_{\mathcal{H}} + \lvert\lvert (f-u_{n}) - (f-u_{m})\rvert\rvert^2_{\mathcal{H}}  \\
>>> &= \lvert\lvert 2f-u_{n}-u_{m}\rvert\rvert^2_{\mathcal{H}} + \lvert\lvert u_{m} - u_{n}\rvert\rvert^2_{\mathcal{H}}  \\
>>> &= 4\left\lvert \left\lvert  f - \frac{u_{n}+u_{m}}{2}  \right\rvert \right\rvert ^2_{\mathcal{H}} +  \left\lvert \left\lvert  u_{m} - u_{n} \vphantom{\frac{1}{1}} \right\rvert \right\rvert^2_{\mathcal{H}} 
>>>\end{align} $$
>>>Substituting this result into the relation $(3)$ gives
>>>$$\begin{align}
>>> 0 &\leq 4\left\lvert \left\lvert  f - \frac{u_{n}+u_{m}}{2}  \right\rvert \right\rvert ^2_{\mathcal{H}} +  \left\lvert \left\lvert  u_{m} - u_{n} \vphantom{\frac{1}{1}} \right\rvert \right\rvert^2_{\mathcal{H}} - 4\alpha^2 < \frac{2}{n}+\frac{2}{m} \\ 
>>> 0 &\leq 4\Bigg(\left\lvert \left\lvert  f - \frac{u_{n}+u_{m}}{2}  \right\rvert \right\rvert ^2_{\mathcal{H}} - \alpha^2 \Bigg) +  \left\lvert \left\lvert  u_{m} - u_{n} \vphantom{\frac{1}{1}} \right\rvert \right\rvert^2_{\mathcal{H}}< \frac{2}{n}+\frac{2}{m}
>>>\end{align}$$
>>>Note, $U$ is convex, hence $\frac{u_{n}+u_{m}}{2}\in U$. Therefore, we know that the best approximation in $U$ **must be** less or equal to the distance $\left\lvert \left\lvert  f - \frac{u_{n}+u_{m}}{2}  \right\rvert \right\rvert$. We can state and make the following observation
>>>$$0 \leq 4\Bigg(\underbrace{ \left\lvert \left\lvert  f - \frac{u_{n}+u_{m}}{2}  \right\rvert \right\rvert ^2_{\mathcal{H}} }_{ \geq\delta(f,U)^2 } - \underbrace{ \alpha^2 }_{ =\delta(f,U)^2 } \Bigg) +  \left\lvert \left\lvert  u_{m} - u_{n} \vphantom{\frac{1}{1}} \right\rvert \right\rvert^2_{\mathcal{H}}< \frac{2}{n}+\frac{2}{m}$$
>>>We note, that there must be some remainder $\gamma>0$
>>>$$\begin{align}
>>> 0 &\leq 4\gamma + \lvert\lvert u_{m}-u_{n} \rvert\rvert^2_{\mathcal{H}}  \\
>>>   &<   \lvert\lvert u_{m}-u_{n} \rvert\rvert^2_{\mathcal{H}}  \\
>>> &< \frac{2}{n} + \frac{2}{m}
>>>\end{align}$$
>>>Hence, we arrive finally at the relation of
>>>$$\lvert\lvert u_{m}-u_{n} \rvert\rvert^2_{\mathcal{H}} < \frac{2}{n}+\frac{2}{m} $$
>>>which defines Cauchy sequences for $\{ u_{n} \}_{n=1}^\infty$ and $\{ u_{m} \}_{m=1}^\infty$ as they approach $0$ as $n,m$ increase, i.e.
>>>$$\lvert\lvert u_{m}-u_{n} \rvert\rvert^2_{\mathcal{H}}  \underset{m,n \to \infty}\longrightarrow 0$$
>>>Since we identified $\{ u_{n} \}_{n=1}^\infty$ to be a Cauchy sequence in $U$ and $U$ is closed, we know that the best approximation exists and is in $U$.$$\tag*{$\checkmark$}$$
>>
>>3. Show $P:H \to U$ is continuous
>>
>>>Omitted for now
>>
>>$$\tag*{$\square$}$$

>[!theorem] Projection Theorem
>Let $\mathcal{H}$ be a Hilbert space and $U \subset \mathcal{H}$ a closed subspace.
>1. Let $f \in \mathcal{H}$ and $g_{0}=P(f)$ be the best approximation of $f$ in $U$, i.e.
>$$\lvert\lvert f - g_{0} \rvert\rvert_{\mathcal{H}} = \delta(f,U)$$
>Then it holds $f-g_{0} \in U^\perp$, i.e.
>$$f-g_{0} \perp U: \left\langle f-g_{0}\,,\,u \right\rangle=0 \;\; \forall u\in U $$
>
>>[!proof]- Proof (Indirect)
>> Assume $$f - \underbrace{ P(f) }_{ =g_{0} } \not\in U^\perp$$
>> Then there exists some $u \in U$ which is not orthogonal to $f-P(f)$
>> $$\exists u \in U: u \neq 0: \left\langle u\,,\,f-P(f) \right\rangle \neq 0 $$
>> We denote
>> $$\begin{align} 
>> h:&= f - P(f) \\
>> \alpha:&= \left\langle u\,,\,h \right\rangle \neq 0  \\
>> \lambda &\in \mathbb{K}
>>\end{align}$$
>>We do the following calculation with $(\underbrace{ P(f) }_{ \in U }+ \underbrace{ \lambda u }_{ \in U }) \in U$
>>$$\begin{align}
>> \lvert\lvert f - \big(P(f)+\lambda u\big) \rvert\rvert_{\mathcal{H}}^2 &= \lvert\lvert \underbrace{ \big(f - P(f)\big) }_{ =h } - \lambda u \rvert\rvert \\
>> &= \left\langle h-\lambda u\,,\, h - \lambda u \right\rangle     \\
>> &= \left\langle h\,,\,h \right\rangle - \lambda \left\langle u\,,\,h \right\rangle + \left\langle  h\,,\,-\lambda u \right\rangle + \left\langle -\lambda u\,,\,-\lambda u \right\rangle \\
>> &= \lvert\lvert h \rvert\rvert_{\mathcal{H}}^2 - \lambda \left\langle u\,,\,h \right\rangle - \overline{\lambda}\left\langle h\,,\,u \right\rangle + \underbrace{ \lvert \lambda \rvert^2 }_{ =\lambda \cdot \overline{\lambda} } \lvert\lvert u \rvert\rvert_{\mathcal{H}}^2  \\
>> &= \lvert\lvert h \rvert\rvert_{\mathcal{H}}^2 - 2\mathrm{Re}(\lambda \underbrace{ \left\langle u\,,\,h \right\rangle }_{ =\alpha } ) + \lvert \lambda \rvert ^2 \lvert\lvert u \rvert\rvert _{\mathcal{H}}^2
>>\end{align}$$
>>We choose $\lambda= \dfrac{\overline{\alpha}}{\lvert\lvert u \rvert\rvert^2_{\mathcal{H}}}$
>>$$\begin{align}
>> \phantom{\lvert\lvert f - \;\;\;\;\;} &= \lvert\lvert h \rvert\rvert _{\mathcal{H}}^2 - 2\mathrm{Re}\left( \frac{\overline{\alpha}\cdot\alpha}{\lvert\lvert u \rvert\rvert^2_{\mathcal{H}}} \right) + \frac{\lvert \alpha \rvert^2 }{\lvert\lvert u \rvert\rvert_{\mathcal{H}}^2 } \\
>> &= \lvert\lvert h \rvert\rvert ^2_{\mathcal{H}} - \frac{2\lvert \alpha \rvert^2 }{\lvert\lvert u \rvert\rvert ^2_{\mathcal{H}}} + \frac{\lvert \lambda \rvert^2 }{\lvert\lvert u \rvert\rvert^2_{\mathcal{H}} } \\
>> &= \lvert\lvert h \rvert\rvert ^2_{\mathcal{H}} - \frac{\lvert \alpha \rvert^2 }{\lvert\lvert u \rvert\rvert ^2_{\mathcal{H}}} \\
>> &= \lvert\lvert f -P(f) \rvert\rvert _{\mathcal{H}}^2 - \underbrace{ \frac{\lvert \alpha \rvert^2 }{\lvert\lvert u \rvert\rvert ^2_{\mathcal{H}}} }_{ >0 }  \\
>> &< \lvert\lvert f - P(f) \rvert\rvert ^2_{\mathcal{H}} 
>>\end{align}$$
>>Since this is a contradiction and $P(f)$ is best approximation of $f$ in $U$, we have
>>$$f-P(f) \in U^\perp \tag*{$\square$}$$
>
>2. For any $f \in \mathcal{H}$ there exists a unique representation
>$$f = u + v$$
>where $u \in U, v \in U^\perp$, hence
>$$H = U \oplus U^\perp \tag{Orthogonal Sum}$$
>
>>[!proof]-
>>1. Existence
>>
>>>Let $f \in \mathcal{H}$, then we know by 1) 
>>>- $\exists u \in U$ with $u = P(f)$
>>>- $v:= f-P(f) \in U^\perp$
>>>
>>>Inserting into $v$ our definition of $P(f)$ we get
>>>$$v = f - u \iff f = v + u$$
>>
>>2. Uniqueness
>>
>>> Assume there exist two different representations $u_{1},u_{2} \in U$ and $v_{1},v_{2} \in U^\perp$ with
>>> $$f = u_{1}+v_{1} = u_{2} + v_{2}$$
>>> Rearranging the decompositions gives
>>> $$u_{1}-u_{2} = v_{1} - v_{2}$$
>>> We know $u_{1}-u_{2} \in U$ and $v_{1} - v_{2} \in U^\perp$. Note, since both are equal and both are from different spaces, we can conclude $$(v_{1}-v_{2}),(u_{1}-u_{2}) \in U \cap U^\perp = \{ 0 \}$$
>>>>[!recall] [[B1 - Hilbert Spaces#^2f6a37|Recall Remark in Definition of Orthogonality]]
>>>
>>>Hence, 
>>>$$\begin{align}
>>>u_{1}-u_{2} &= 0 \implies u_{1} = u_{2} \\
>>>v_{1}-v_{2} &= 0 \implies v_{1}=v_{2}  
>>>\end{align}$$
>>> Therefore, the orthogonal decomposition is unique $$\tag*{$\square$}$$

^312b54

>[!lemma] Corollary
>Let $\mathcal{H}$ be an Hilber Space and $U \subset H$ a subspace of $\mathcal{H}$. Then it holds
>$$(U^\perp)^\perp = \overline{U}$$
>In particular, if $U^\perp = \{ 0 \}$ then $U$ is dense in $\mathcal{H}$, i.e. $\overline{U}= \mathcal{H}$
>>[!proof]-
>>Note, $\overline{U} \subset \mathcal{H}$ is a closed subspace of $\mathcal{H}$. We know by the [[#^312b54| Projection Theorem (ii)]] 
>>$$H = \overline{U} \oplus (\overline{U})^\perp$$
>>By [[B1 - Hilbert Spaces#^4c0a6a| properties of orthogonality (ii)]] we know $(\overline{U})^\perp = U^\perp$, therefore
>>$$H = \overline{U} \oplus U^\perp$$
>>Lets redefine $\overline{U}=:V$ to make clear we want to rethink the nature of $V$
>>$$H = V \oplus U^\perp$$
>>We know by [[B1 - Hilbert Spaces#^4c0a6a| properties of orthogonality (ii)]] that $U^\perp$ is closed, and the $V = (U^\perp)^\perp$, which establishes the identity
>>$$(U^\perp)^\perp = \overline{U} \tag*{$\square$}$$

>[!def] Definition Orthogonal Projection
>Let $\mathcal{H}$ be a Hilbert space and $U \subset H$ a closed subspace. Then we call
>$$\begin{align}
> P_{h}:& H \to U \\
> P_{h}:& f \mapsto P_{h}f = g \in U
>\end{align}$$
>with $f - P_{h}f \in U^\perp$ being the **orthogonal projection** of $\mathcal{H}$ onto $U$.

>[!property] Properties of the Orthogonal Projection
>- $P_{h}$ is continuous
>- $P_{h}$ is linear
>- $P_{h}^2 = P_{h}$
>- $\lvert\lvert P_{h} \rvert\rvert_{\mathcal{L}(\mathcal{H})}=1$
>- $N(P_{h})= U^\perp$ with $N$ being the Nullspace and $N(P_{h})=\{ g \in \mathcal{H} \; | \; P_{h}g=0 \}$