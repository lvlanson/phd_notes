---
aliases:
- Anisotropic QUIPS Analysis
---
Based on the paper of [[../../Literature/@guo2020|Anisotropic QUIPS Paper]]

>[!def] _Geometric Residual Errors_
> Let $\mathbf{x}, \mathbf{u} \in \mathbb{R}^d$ denote a data point and its quantized codebook vector
> ###### Parallel Residual Error
> $$r_{||}(\mathbf{x}, \mathbf{u}) = \frac{\langle( \mathbf{x} - \mathbf{u} ), \; \mathbf{x} \rangle \, \mathbf{x}}{||\mathbf{x}||^2} $$
>
> ###### Orthogonal Residual Error
> $$r_{\perp}(\mathbf{x}, \mathbf{u}) = (\mathbf{x} - \mathbf{u}) - r_{||}(\mathbf{x}, \mathbf{u}) $$

>[!theorem]
>Let $\mathbf{x}, \mathbf{u} \in \mathbb{R}^d$ denote a data point and quantization regarding a query $\mathbf{q} \in \mathbb{R}^d$. Further denote $w:\mathbb{R} \rightarrow  \mathbb{R}^+$ as weighting function. The loss can be computed as follows
>$$ \begin{align}
>l(\mathbf{x}, \mathbf{u}, w) &= h_{||}(w, ||\mathbf{x}||) \cdot ||\mathbf{r}_{||}(\mathbf{x}, \mathbf{u})||² \\
>&+h_{\perp}(w, ||\mathbf{x}||)\cdot ||\mathbf{r}_{\perp}(\mathbf{x}, \mathbf{u})||²
>\end{align}$$
>with
>$$\begin{align}
>h_{||}(w, ||\mathbf{x}||)&:=(d-1)\int\limits_{0}^{\pi}w\Big(||\mathbf{x}||\, \cos\theta\Big)\cdot\Big(\sin^{d-2}\theta - \sin^d \theta\Big) \quad d\theta\\
>h_{\perp}(w, ||\mathbf{x}||)&:=\int\limits_{0}^{\pi}w\Big(||\mathbf{x}||\, \cos\theta\Big) \sin^d\theta \quad d\theta
>\end{align}$$

>[!proof]
>>[!lemma]
>>Let $\mathbf{x}, \mathbf{u} \in \mathbb{R}^d$ denote a data point and its quantizer. If the query $\mathbf{q}$ is uniformly spherically distributed, then
>>$$\begin{align}\mathbb{E}\left[\langle \mathbf{q}, \mathbf{x} - \mathbf{u}\rangle \, | \, \langle\mathbf{q},\mathbf{u}\rangle = t\right] &= \frac{t^2}{||\mathbf{x}||^2} \cdot ||\mathbf{r}_{||}(\mathbf{x}, \mathbf{u})||^2 \\&+ \frac{1-\frac{t^2}{||\mathbf{x}||^2}}{d-1}\cdot ||\mathbf{r}_{\perp}(\mathbf{x},\mathbf{u})||^2\end{align}$$
>
>>[!proof]
>>First note
>>* $\mathbf{q}:= \mathbf{q}_{\perp} + \mathbf{q}_{||}$ the [[../Mathematic Basics/Orthogonal Projection|orthogonal decomposition]] of $\mathbf{q}$ with respect to $\mathbf{x}$
>>* $\mathbf{q}_{||} = \frac{\langle\mathbf{q},\mathbf{x}\rangle\mathbf{x}}{||\mathbf{x}||^2}$ which is parallel to $\mathbf{x}$
>>* $\mathbf{q}_{\perp}=\mathbf{q} - \mathbf{q}_{||}$ which is orthogonal to $\mathbf{x}$
>>* $\mathbf{r}_{||}(\mathbf{x},\mathbf{u}):=\mathbf{r}_{||}$ which is parallel to $\mathbf{x}$
>>* $\mathbf{r}_{\perp}(\mathbf{x},\mathbf{u}):=\mathbf{r}_{\perp}$ which is orthogonal to $\mathbf{x}$
>>
>> The expectation of the inner product of a query $\mathbf{q}$ and !!!!!!!!!! can be computed as
>> $$\begin{align}
>> &\mathbb{E}\Big[\langle\mathbf{q}, \mathbf{x}-\mathbf{u}\rangle^2 \, | \, \langle \mathbf{q}, \mathbf{x} \rangle = t\Big] \\
>> = &\mathbb{E}\Big[\langle\mathbf{q}_{||} + \mathbf{q}_{\perp}, \mathbf{r}_{||}+\mathbf{r}_{\perp}\rangle^2 \, | \, \langle \mathbf{q}, \mathbf{x} \rangle = t\Big]\\
>> = &\mathbb{E}\Big[\big(\langle\mathbf{q}_{||},\mathbf{r}_{||}\rangle + \langle\mathbf{q}_{\perp}, \mathbf{r}_{\perp}\rangle\big)^2 \, | \, \langle \mathbf{q}, \mathbf{x} \rangle = t\Big] \\
>> = &\mathbb{E}\Big[\langle\mathbf{q}_{||},\mathbf{r}_{||}\rangle^2 \, | \, \langle \mathbf{q}, \mathbf{x} \rangle = t\Big] + 2\cdot\mathbb{E}\Big[\underbrace{\langle\mathbf{q}_{\perp}, \mathbf{r}_{\perp}\rangle\langle\mathbf{q}_{||},\mathbf{r}_{||}\rangle}_{=0?} \, | \, \langle \mathbf{q}, \mathbf{x} \rangle = t\Big]+\mathbb{E}\Big[\langle\mathbf{q}_{\perp}, \mathbf{r}_{\perp}\rangle^2 \, | \, \langle \mathbf{q}, \mathbf{x} \rangle = t\Big] \\
>> \end{align}$$



```tikz
\begin{document}
\begin{tikzpicture}
\draw[draw=none] (0,-7) rectangle (0.1,7); %create a bounding box to reserve space
\begin{pgflowlevelscope}{\pgftransformscale{3}}
\shade[ball color = gray!40, opacity = 0.4] (0,0) circle (2cm);
\draw (0,0) circle (2cm);
\draw (-2,0) arc (180:360:2 and 0.6);
\draw[dashed] (2,0) arc (0:180:2 and 0.6);

% points
\fill[fill=black] (0,0) circle (1pt);
\fill[fill=black] (1,1) circle (1pt) node[anchor=south]{$x$};
\fill[fill=black] (-1.2,0.9) circle (1pt) node[anchor=east]{$u$};

%lines
\draw(1,1) -- node[above]{$u-x$} (-1.2,0.9);
\draw[->](0,0) -- (1,1);
\draw[->](0,0) -- (-1.2,0.9);
%\draw(0,0) -- node[right, yshift=-2ex, xshift=-1ex]{$-r_{||}$}(-1.149, -1.149);
%\draw(0,0) -- node[left, yshift=-2ex, xshift=2ex]{$r_{\perp}$} (1.05, -1.049);
%\draw(0,0) -- (1,1);

%measure
\draw[dashed] (0,0 ) -- node[above]{$r$} node[below]{\tiny{$||r||=1$}} (2,0);
\end{pgflowlevelscope}
\end{tikzpicture}
\end{document}
```

```python
import numpy as np

# initializing x as datapoint and u as quantizer
x = np.array([1,1], dtype=np.float16)
u = np.array([-1.2,0.9], dtype=np.float16)

# calculating parallel residual error
r_par = (np.dot(x-u, x) * x) / (np.linalg.norm(x)**2)
print("Parallel Residual Error:", r_par)

# calculating orthogonal residual error
r_orth = (x - u) - r_par
print("Orthogonal Residual Error:", r_orth)
```

