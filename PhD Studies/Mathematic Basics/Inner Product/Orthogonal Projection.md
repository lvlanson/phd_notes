---
aliases:
  - Orthogonal Projection
  - orthogonal projection
  - orthogonal decomposition
---
Let $\mathbf{x}, \mathbf{u} \in H$ denote vectors equipped with an [[Inner Product/Inner Products|inner product]] $\langle . \, , \, . \rangle$.

>[!def] Parallelity
> Two vectors $\mathbf{x}, \hat{\mathbf{x}} \in H$ are parallel if
> $$ \mathbf{x} = \alpha \hat{\mathbf{x}}$$
> for some $\alpha \in \mathbb{K}$

>[!def] Orthogonality
>Two vectors $\mathbf{x}, \hat{\mathbf{x}} \in H$ are orthogonal if
>$$ \langle \mathbf{x}, \hat{\mathbf{x}} \rangle = 0$$

>[!pic]
>```tikz
\begin{document}
\begin{tikzpicture}
\draw[draw=none] (0,0) rectangle (11,11); %create a bounding box to reserve space
\begin{pgflowlevelscope}{\pgftransformscale{2}}
>
% Grid
\draw[very thin,gray] (0,0) grid (5,5);
\draw[thick,->] (0,0) -- (0,5) node[anchor=south east]{$x_2$};
\draw[thick,->] (0,0) -- (5,0) node[anchor=north west]{$x_1$};
>
% Vectors
\draw[thick,->] (0,0) -- (1,4) node[anchor=south east]{$\mathbf{x}$};
\draw[thick,->] (0,0) -- (4,2) node[anchor=north west]{$\mathbf{u}$};
\draw[thick,->, teal] (0,0) -- (2.4,1.2) node[anchor=north, yshift=-1ex]{$\alpha\mathbf{u}$};
\draw[thick,->, lime] (2.4, 1.2) -- (1,4) node[anchor=west, yshift=-9ex, xshift=5ex]{$\mathbf{z}$} ;
>
\end{pgflowlevelscope}
\end{tikzpicture}
\end{document}
>```
> ${}$ 
>With $\alpha\mathbf{u}$ being the orthogonal projection of $\mathbf{x}$ onto $\mathbf{u}$. Note $\mathbf{x} = \mathbf{z} + \alpha\mathbf{u}$

# Deriving the Orthogonal Projection

First find the $\alpha \in \mathbb{K}$ such that we find the parallel component of $\mathbf{u}$
$$ \begin{align}
\langle \mathbf{z}, \mathbf{u} \rangle &= 0 \\
\langle \mathbf{x} - \alpha \mathbf{u}, \mathbf{u} \rangle &= 0 \\
\langle \mathbf{x}, \mathbf{u} \rangle - \langle \alpha \mathbf{u}, \mathbf{u} \rangle &= 0 \\
\langle \mathbf{x}, \mathbf{u} \rangle - \alpha\langle \mathbf{u}, \mathbf{u} \rangle &= 0 \\
\alpha\langle \mathbf{u}, \mathbf{u} \rangle &= \langle \mathbf{x}, \mathbf{u} \rangle \\
\alpha &= \frac{\langle \mathbf{x}, \mathbf{u} \rangle}{\langle \mathbf{u}, \mathbf{u} \rangle} \\
&= \frac{\langle \mathbf{x}, \mathbf{u} \rangle}{||\mathbf{u}||^2} \\
\end{align}$$

Orthogonal projection is the scaling of $\mathbf{u}$ with $\alpha$, hence

$$\begin{align}
	\alpha \mathbf{u} = \frac{\langle \mathbf{x}, \mathbf{u} \rangle}{||\mathbf{u}||^2} \mathbf{u}
\end{align}$$

And $\mathbf{z}$ can be found by decomposing

$$\begin{align}
\mathbf{x}&=\alpha\mathbf{u} + \mathbf{z} \\
\mathbf{z}&= \mathbf{x} - \alpha\mathbf{u}
\end{align}$$

>[!code]-
>```python
import numpy as np
>
x = np.array([1,4])
u = np.array([4,2])
>
alpha_u = (np.dot(x,u)*u)/(np.linalg.norm(u)**2)
print("Orthogonal Projection of x onto u", proj)
z = x - alpha_u
print("Orthogonal Complement of x and the Orthogonal Projection", z)
>```