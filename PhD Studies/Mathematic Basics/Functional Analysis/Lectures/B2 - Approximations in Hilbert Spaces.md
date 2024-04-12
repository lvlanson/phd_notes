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
>>[!proof]
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
>>>Denote $f_{0} \in \mathcal{H}$ and
>>>$$P(f_{0}) = g_{0} \iff \lvert\lvert f_{0}-g_{0} \rvert\rvert_{H}=\delta(f_{0},U) $$
>>>To show continuity we use the [[Ax Continuity#^dbc5ec| definition of continuity]], i.e.
>>>$$\forall \varepsilon > 0 : \exists \phi_{\varepsilon}>0: \forall f_{1} \in \mathcal{H} \text{ such that } \lvert\lvert f_{1}-f_{0}  \rvert\rvert< \phi_{\varepsilon} \implies \lvert\lvert \underbrace{ P(f_{1}) }_{ =: g_{1} }-\underbrace{ P(f_{0}) }_{ =: g_{0} } \rvert\rvert < \varepsilon  $$
>>>and will use the property of Cauchy sequences as in the previous part. Therefore, denote
>>>$$\begin{align}
>>> \varepsilon &> 0 \\
>>> \mu&\leq \delta(f_{0}, U) \\
>>> \varepsilon' &= \frac{\varepsilon}{1+\mu}  
>>>\end{align}$$
>>>By assumption we have
>>>$$\lvert\lvert f_{0}-g_{0} \rvert\rvert_{\mathcal{H}} $$