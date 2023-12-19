---
aliases:
  - Inner Products
  - Dot Product
  - Semi-Inner Product
  - Quasi-Inner Product
  - Generalized Semi-Inner Product
  - inner product
---

>[!def] Inner Product
>Let $H$ be a vector space over $\mathbb{F}$. An <u>inner product</u> on $H$ is a function $\langle\, . \,, \, . \,\rangle$ from $H \times H$ into $\mathbb{F}$ such that for all $\mathbf{x},\mathbf{y},\mathbf{z} \in H$ and $\lambda \in \mathbb{F}$ 
>$$\begin{alignat}{2}
&\text{(i)}  \;&&\langle x,y\rangle = \overline{\langle y,x \rangle} \\
&\text{(ii)} \;&&\langle x + z, y \rangle =  \langle x,y \rangle + \langle z,y \rangle \\
& &&\langle \lambda x,y \rangle = \lambda \langle x,y \rangle \\
&\text{(iii)}\;&&  \langle x,x \rangle \geq 0 \\
& &&\langle x,x \rangle = 0 \iff x=0
\end{alignat}$$

---

>[!def] Semi-Inner Product
>Let $X$ be a vector space over $\mathbb{F}$. A <u>semi-inner product</u> on $X$ is a function $[ . \,,\, . ]$ from $X \times X$ into $\mathbb{F}$ such that for all $\mathbf{x}, \mathbf{y}, \mathbf{z} \in H$ and $\lambda \in \mathbb{F}$
>$$\begin{alignat}{2}
&\text{(i)} \;&&[ x + z, y ] =  [ x,y ] + [ z,y ] \\
& &&[ \lambda x,y ] = \lambda [ x,y ] \\
&\text{(ii)}\;&&  [x,x] > 0  \text{ for } x \neq 0\\
&\text{(iii)}  \;&&\left\vert[ x,y ]\right\vert^2 \leq [ x,x ] [y,y] \\
\end{alignat}$$

>[!note]-
>In the **Semi-Inner Product** property (iii) is called the <u>Cauchy-Schwartz Inequality</u> 

---

>[!def] Generalized Semi-Inner Product
>Let $X$ be a vector space over $\mathbb{F}$. A <u>semi-inner product</u> on $X$ is a function $[ . \,,\, . ]$ from $X \times X$ into $\mathbb{F}$ such that for all $\mathbf{x}, \mathbf{y}, \mathbf{z} \in H$ and $\lambda \in \mathbb{F}$
>$$\begin{alignat}{2}
&\text{(i)} \;&&[ x + z, y ] =  [ x,y ] + [ z,y ] \\
& &&[ \lambda x,y ] = \lambda [ x,y ] \\
&\text{(ii)}\;&&  [x,x] > 0  \text{ for } x \neq 0\\
&\text{(iii)}  \;&&\left\vert[ x,y ]\right\vert \leq [ x,x ]^{\frac{1}{p}} [y,y]^{\frac{p-1}{p}} \;\text{ for }\; 1 < p < \infty\\
\end{alignat}$$

>[!note]-
>In the **Generalized Semi-Inner Product** property (iii) is called the <u>Hölder's Inequality</u>

---