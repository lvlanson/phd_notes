>[!theorem] Rolle's Theorem ([[../../../PDFs/briggs2019.pdf#page=276| Source]])
>Let $f$ be continuous on a closed interval $[a,b]$ and differentiable on $(a,b)$ with $f(a) = f(b)$. There is at least one point $c$ in $(a,b)$ such that $f'(c) = 0$.
>
>![[figures/rolles_theorem.png | 350]]
>>[!proof]-
>>><u>Case 1:</u>
>>>Suppose $f$ attains both its absolute maximum and minimum values at the endpoints. Since $f(a) = f(b)$ the maximum and minimum are equal, and it follows that $f$ is a constant function, i.e. $f'(x) = 0$ for all $x \in (a,b$.
>>
>>><u>Case 2:</u>
>>>Assume at least one of the absolute extreme values of $f$ does not occur at an end-point, then $f$ must attain an absolute extreme value at an interior point of $[a,b]$. Therefore, $f$ must have either a local maximum or a local minimum at point $c \in (a,b)$.  An extremum $(x_{E}, y_{E})$ is known to satisfy
>>>$$ f'(x_{E})=0$$
>>>Therefore there exists some point with $f'(c)=0$ $$\begin{align}
>>> \,\tag*{$\square$}
>>>\end{align}$$

^5732a4

>[!theorem] Mean Value Theorem ([[../../../PDFs/briggs2019.pdf#page=277| Source]])
> If $f$ is continuous on the closed interval $[a,b]$ and differentiable on $(a,b)$, then there is at least on point $c$ in $(a,b)$ such that
> $$\frac{f(b)-f(a)}{b-a} = f'(c)$$
> 
> ![[figures/mean_value_theorem_real.png | center]]
>>[!proof]-
>> Note the secant line passes through the points $(a, f(a))$ and $(b, f(b))$. Let the secant line be described by the function $l(x)$. Further, we define a function $g(x)$ which measures the difference between the secant line and the original graph, i.e.
>> $$g(x) = f(x) - l(x)$$
>> Since $f$ and $l$ are continuous on $[a,b]$ and differentiable on $(a,b)$, it follows $g$ must also be continuous on $[a,b]$ and differentiable on $(a,b)$. Note, that both functions intersect at $f(a) = l(a)$ and $f(b) = l(b)$. Therefore we can state
>> $$\begin{alignat}{2}
>> g(a) &= f(a)-l(a)  &&= 0\\
>> g(b) &= f(b)-l(b) &&= 0
>>\end{alignat}$$
>>Hence, equation $g(x)$ fulfills the condition of [[Differentiation Statements#^5732a4|Rolle's Theorem]]. Thus, there exists a point $c \in (a,b)$ such that $g'(c) = 0$.  Differentiating on both sides of $g$ we have
>>$$ g'(c) = f'(c) - l'(c) = 0$$
>>By this assertion we can conclude
>>$$ \begin{align}
>> f'(c) = l'(c) \tag{1}
>>\end{align} $$
>>Now we determine $l'(c)$. Note, the derivative of $l'(c)$ is the slope of the secant line. By definition, it is
>>$$l'(c) = \frac{f(b)-f(a)}{b-a}$$
>>From the result of equation $(1)$ we can conclude
>>$$ \begin{align}
>> f'(c) = \frac{f(b)-f(a)}{b-a} \tag*{$\square$}
>>\end{align}$$

^71d429

