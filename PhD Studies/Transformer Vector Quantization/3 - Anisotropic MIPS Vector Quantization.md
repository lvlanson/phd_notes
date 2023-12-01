---
aliases:
  - Anisotropic QIPS
---

All information regarding this topic can be found in [[../../Literature/@guo2020|Anisotropic QUIPS Paper]]
>[!paper]-
>![[../../Literature/@guo2020|Anisotropic QUIPS Paper]]
### <font color="red">Problem</font>
> Cost function (MSE) learns to represent dataspace distribution, *i.e. minimizing the reconstruction error*, but for **[[1 - Maximum Inner Product Search|MIPS]]** it's important to learn maximizing the score for respective queries, *i.e. larger [[../Mathematic Basics/Inner Product/Inner Products|inner products]]*

### <font color="red">Solution</font>
> Create cost function which penalizes parallelity more than orthogonality 

>[!def] Score-Aware Quantization Loss
> Let $\mathbf{x}, \mathbf{u} \in \mathbb{R}^d$ denote a data point and its quantized codebook vector with respect to the query $\mathbf{q} \in \mathbb{R}^d$. Further, assume $\mathbf{q}$ is uniformly spherically distributed with distribution $\mathcal{Q}$. Denote $w: \mathbb{R} \rightarrow \mathbb{R}^+$ The loss function is given as
> $$l(\mathbf{x},\mathbf{u},w) = \mathbb{E}_{q \sim \mathcal{Q}}\left[w(\langle\mathbf{q},\mathbf{x}\rangle)\,\langle\mathbf{q},\mathbf{x}-\mathbf{u}\rangle^2\right]$$

>[!note]-
> * $\langle \mathbf{q}, \mathbf{x}\rangle$ denotes the inner product of MIPS
> * $w(\langle \mathbf{q}, \mathbf{x}\rangle)$ denotes the positive definite weight mapping
> * $\langle\mathbf{q},\mathbf{x}-\mathbf{u}\rangle$ if $\mathbf{x}$ and $\mathbf{u}$ denotes the projection length of $\mathbf{q}$ onto $\mathbf{x-u}$

>[!def] Geometric Residual Errors
> Let $\mathbf{x}, \mathbf{u} \in \mathbb{R}^d$ denote a data point and its quantized codebook vector
> ###### Parallel Residual Error
> $$r_{||}(\mathbf{x}, \mathbf{u}) = \frac{\langle( \mathbf{x} - \mathbf{u} ), \; \mathbf{x} \rangle \, \mathbf{x}}{||\mathbf{x}||^2} $$
>
> ###### Orthogonal Residual Error
> $$r_{\perp}(\mathbf{x}, \mathbf{u}) = (\mathbf{x} - \mathbf{u}) - r_{||}(\mathbf{x}, \mathbf{u}) $$

>[!note]-
> $\mathbf{r}_{||}$ is the [[../Mathematic Basics/Inner Product/Orthogonal Projection|orthogonal projection]] of $\mathbf{x-u}$ onto $\mathbf{x}$

>[!note]-
><u>Parallel Error:</u>
 If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **parallel** --> $r_{||} = \alpha \mathbf{x} = \mathbf{x} - \mathbf{q}$
 If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **orthogonal** --> $r_{||} = \mathbf{0}$
 >
 <u>Orthogonal Error:</u>
 >If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **parallel** --> $r_{\perp} = (\mathbf{x} - \mathbf{u}) - (\mathbf{x} - \mathbf{u})$
 > If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **orthogonal** --> $r_{\perp} = \alpha \mathbf{x} = \mathbf{x} - \mathbf{q} - \mathbf{0}$

>[!pic]-
>```tikz
\begin{document}
\begin{tikzpicture}
\draw[draw=none] (-7,-4) rectangle (11,11); %create a bounding box to reserve space
\begin{pgflowlevelscope}{\pgftransformscale{2}}
>
% Grid
\draw[very thin,gray] (-4,-2) grid (5,5);
\draw[thick,->] (0,-2) -- (0,5) node[anchor=south east]{$x_2$};
\draw[thick,->] (-4,0) -- (5,0) node[anchor=north west]{$x_1$};
>
% Vectors
\draw[thick,->, gray] (0,0) -- (1,4) node[anchor=south east]{$\mathbf{x}$};
\draw[thick,->, gray] (0,0) -- (3,1) node[anchor=north west]{$\mathbf{u}$};
\draw[thick,->,red] (0,0) -- (-2,3) node[yshift=-9ex, xshift=-2.5ex, anchor=west]{$\mathbf{x} - \mathbf{u}$};
\draw[thick,->,lime] (0,0) -- (0.588235,2.352) node[yshift=-8ex, xshift=-1.5ex, anchor=west] {$\mathbf{r}_{||}$};
\draw[thick,->,teal] (0,0) -- (-2.588, 0.6484) node[yshift=0.5ex, xshift=8ex, anchor=west] {$\mathbf{r}_{\perp}$};
>
\end{pgflowlevelscope}
\end{tikzpicture}
\end{document}
>```
>Figure 1: Residual Errors between $\mathbf{x}$ and $\mathbf{x}-\mathbf{u}$. The quantization error of $\mathbf{x}$ and $\mathbf{u}$ are decomposed into the parallel error $\mathbf{r}_{||}$ and the orthogonal error $\mathbf{r}_{\perp}$. 
>$$\begin{align}
\mathbf{x}&=(1,4)\\
\mathbf{u}&=(3,1)\\
\mathbf{r}_{||}&=(0.588235,2.352) \\
\mathbf{r}_{\perp}&=(-2.588, 0.6484)
\end{align}$$
>
>```tikz
\begin{document}
\begin{tikzpicture}
\draw[draw=none] (-7,-4) rectangle (11,11); %create a bounding box to reserve space
\begin{pgflowlevelscope}{\pgftransformscale{2}}
>
% Grid
\draw[very thin,gray] (-4,-2) grid (5,5);
\draw[thick,->] (0,-2) -- (0,5) node[anchor=south east]{$x_2$};
\draw[thick,->] (-4,0) -- (5,0) node[anchor=north west]{$x_1$};
>
% Vectors
\draw[thick,->, gray] (0,0) -- (1,4) node[anchor=south east]{$\mathbf{x}$};
\draw[thick,->, gray] (0,0) -- (3,1) node[anchor=north west]{$\mathbf{u}$};
\draw[thick,<-,red] (1,4) -- (3,1) node[yshift=10ex, xshift=-6ex, anchor=west]{$\mathbf{x} - \mathbf{u}$};
\draw[thick,->,lime] (3,1) -- (3.588235,3.352) node[yshift=-8.5ex, xshift=-0.5ex, anchor=west] {$\mathbf{r}_{||}$};
\draw[thick,->,teal] (3.588,3.352) -- (1,4) node[xshift = 8ex, yshift=0.5ex, anchor=west] {$\mathbf{r}_{\perp}$};
>
\end{pgflowlevelscope}
\end{tikzpicture}
\end{document}
>```
>Figure 2: Rearranging Vectors showing the decomposition and orthogonality property of the residual errors.
>
>>[!Code]-
>> Calculating the **Residual Errors**
>>```python
>>import numpy as np
>>
>> # initializing x as datapoint and u as quantizer
>> x = np.array([1,4], dtype=np.float16)
>> u = np.array([3,1], dtype=np.float16)
>>
>> # calculating parallel residual error
>> r_par = (np.dot(x-u, x) * x) / (np.linalg.norm(x)**2)
>> print("Parallel Residual Error:", r_par)
>> 
>># calculating orthogonal residual error
>>r_orth = (x - u) - r_par
>>print("Orthogonal Residual Error:", r_orth)
>>```
>
>>[!Code]-
>>Calculating Vectors for the illustration
>>```python
>>import numpy as np
>>
>># data points
>>x = np.array([1,4], dtype=np.float16)
>>u = np.array([3,1], dtype=np.float16)
>>
>># residual errors
>>r_par = np.array([0.588, 2.352])
>>r_orth = np.array([-2.588, 0.6484])
>>
>># projections
>>r_par_projection = r_par + u
>>r_orth_projection = r_orth + r_par_projection
>>
>>print("Residual Parallel Projection:", r_par_projection)
>>print("Residual Parallel Projection:", r_orth_projection)
>>```

