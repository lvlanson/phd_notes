### <font color="red">Problem</font>
> Cost function (MSE) learns to represent dataspace distribution, *i.e. minimizing the reconstruction error*, but for **MIPS** its important to learn maximizing the score for respective queries, *i.e. larger inner products*

### <font color="red">Solution</font>
> Create cost function which penalizes parallelity more than orthogonality 

>[!def] _Geometric Residual Errors_
> Let $\mathbf{x}, \mathbf{u} \in \mathbb{R}^d$ denote a data point and its quantized codebook vector
> ###### Parallel Residual Error
> $$r_{||}(\mathbf{x}, \mathbf{u}) = \frac{\langle( \mathbf{x} - \mathbf{u} ), \; \mathbf{x} \rangle \, \mathbf{x}}{||\mathbf{x}||^2} $$
>
> ###### Orthogonal Residual Error
> $$r_{\perp}(\mathbf{x}, \mathbf{u}) = (\mathbf{x} - \mathbf{u}) - r_{||}(\mathbf{x}, \mathbf{u}) $$

>[!note]
><u>Parallel Error:</u>
 If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **parallel** --> $r_{||} = \alpha \mathbf{x} = \mathbf{x} - \mathbf{q}$
 If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **orthogonal** --> $r_{||} = \mathbf{0}$
 >
 <u>Orthogonal Error:</u>
 >If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **parallel** --> $r_{\perp} = (\mathbf{x} - \mathbf{u}) - (\mathbf{x} - \mathbf{u})$
 > If $\mathbf{x}-\mathbf{q}$ and $\mathbf{x}$ are **orthogonal** --> $r_{\perp} = \alpha \mathbf{x} = \mathbf{x} - \mathbf{q} - \mathbf{0}$

