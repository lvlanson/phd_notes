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

>[!theorem] Orthogonal Projection Theorem
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
>>>The strategy for this proof is to construct a contradiction. We assume to have 2 best approximations, and construct by our convexity property another best approximation. We will enforce a contradiction and show, that the constructed best approximation is less than the best approximation by definition. Therefore there only can be one single best approximation. 
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
>>>First note, 
>>>$$\begin{alignat}{2}
>>> \forall \varepsilon>0: \exists \alpha_{\varepsilon}>0 \text{ such that } &\forall f \in \mathcal{H} \text{ and } \forall g_{1}, g_{2} \in U: \\[1em]
>>> \lvert\lvert f-g_{1} \rvert\rvert_{\mathcal{H}} &<  \delta(f,U) + \alpha_{\varepsilon} \tag{i}\\
>>> \lvert\lvert f-g_{2} \rvert\rvert_{\mathcal{H}} &<  \delta(f,U) + \alpha_{\varepsilon} \tag{ii}
>>>\end{alignat}$$