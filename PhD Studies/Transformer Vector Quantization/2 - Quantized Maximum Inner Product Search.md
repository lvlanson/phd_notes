---
aliases:
  - QIPS
---
# QIPS (Quantized Inner Product Search)

Base Information taken from [[../../Literature/@guo2015|QIPS Paper]]

>[!remark]
> Instead of calculating the dot-product over all data-points, *prototypes/codebooks* are trained to represent the data space
>
==> **Dataspace-Compression**

>[!remark]
> For a given query $\mathbf{q} \in \mathbb{R}^d$ and data points $X \subseteq \mathbb{R}^d$ we have  $$  
 \begin{align} 
 \underset{\mathbf{x} \in X}{\text{arg max}} \{ \mathbf{x}^T\mathbf{q}\} &= \underset{\mathbf{x} \in X}{\text{arg max}} \{ ||\mathbf{x}|| \cancel{||\mathbf{q}||} \cos \Theta\}\\
 &= \underset{\mathbf{x} \in X}{\text{arg max}} \{ ||\mathbf{x}|| \cos \Theta\}
 %\underset{\mathbf{x} \in X}{\text{arg max}} \left\{ \frac{1}{2} %\left(||\mathbf{x}||^2 - ||\mathbf{x}||^2 + ||\mathbf{q}||^2 - ||\mathbf{q}||^2 +  2\mathbf{q}^T\mathbf{x}\right)\right\} \\
 %&= \underset{\mathbf{x} \in X}{\text{arg max}} \left\{\left(||\mathbf{x}||^2 + ||\mathbf{q}||^2 - \left(||\mathbf{x}||^2 + ||\mathbf{q}||^2 -  2\mathbf{q}^T\mathbf{x}\right)\right)\right\} \\
 % &= \underset{\mathbf{x} \in X}{\text{arg max}} \left\{ \left(||\mathbf{x}||^2 + ||\mathbf{q}||^2 - || \mathbf{q} - \mathbf{x} ||^2\right)\right\} \\
 %&= \underset{\mathbf{x} \in X}{\text{arg max}} \{ ||\mathbf{x}||^2 - ||\mathbf{x}||^2 \cancel{+ ||\mathbf{q}||^2} -2\mathbf{x}^T\mathbf{q}\}\\  %\underset{\mathbf{x} \in X}{\text{arg max}} \{ \}
%&= \underset{\mathbf{x} \in X}{\text{arg max}} \{ ||\mathbf{x}||^2_2 \; \cos\Theta\}
 \end{align}$$
 >>[!Note]-  
 >>$||\mathbf{q}||$ can be omitted because it does not change the outcome of arg max
 
>[!attention]
>Further we redefine the symbol $K$ from $K$-[[1 - Maximum Inner Product Search|MIPS]]

>[!def] K-Subspaced Dataspace
>
> Let $X \subseteq \mathbb{R}^d$ be a dataset. The dataspace $\mathbb{R}^d$ is subspaced in $K$ subspaces with each having $l =\lceil\frac{d}{K}\rceil$   dimensionality. A vector $\mathbf{x} \in X$ in its $k$-partition will be denoted as $\mathbf{x}^{(k)} \in \mathbb{R}^l$

>[!pic]
Subspacing $\mathbf{x}^{(k)} = \begin{pmatrix} x_{kl+1} \\ \vdots \\ x_{2kl}\end{pmatrix}$ 
>
![[partioning.jpg]]
![[partioning(2).jpg]]

>[!remark]
> If the $d$ is not dividable by $K$ then the last vector will be zero-padded

>[!def] Subspace Quantization
>Let $C_k$ be the amount of codebook vectors for the $k$-th subspace and w.l.g. let $k$ be equal over all subspaces, i.e. $C_k = C$.  Let $\mathbf{U}^{(k)} \in \mathbb{R}^{l \times C}$ be the matrix containing all $C$ codebook vectors $\mathbf{u}^{(k)} \in \mathbb{R}^l$ in the $k$-th partition and $\mathbf{\alpha}^{(k)} \in \{0,1\}^C$ a one-hot encoded vector containing a single $1$. A codebook vector can be obtained with $$ \mathbf{u}^{(k)} = \mathbf{U}^{(k)} \mathbf{\alpha}^{(k)} \approx \mathbf{x}^{(k)}$$
 A maximum inner product search can therefore be approximated with $$ \mathbf{q}^T\mathbf{x} = \sum_{i=1}^K {\mathbf{q}^{(i)}}^T \mathbf{x}^{(i)} \approx \sum_{i=1}^K {\mathbf{q}^{(i)}}^T \mathbf{u}^{(i)}$$

>[!remark] Remark
>Each subspace $k$ will be quantized by $C$ quantizers $\mathbf{u}^{(k)}$. The $k$-th subspace can be illustrated as
$$ \begin{align}
	\mathbf{U} &= \left[\mathbf{u}_1\, \mathbf{u}_2 \, \ldots \, \mathbf{u}_i \, \;\;\;\ldots \, \mathbf{u}_C\right] \\
	\mathbf{\alpha} &= \left[ 0 \quad 0 \;\, \ldots \; 1_{i\text{-th}}\, \ldots \, 0  \;\;\;\right] \\
	\mathbf{U} \mathbf{\alpha}^T &= \left[\mathbf{u}_1\, \mathbf{u}_2 \, \ldots \, \mathbf{u}_i \, \ldots \, \mathbf{u}_C\right] \left[\begin{matrix} 0 \\ 0 \\ \vdots \\ 1_{i\text{-th}}\\ \vdots \\ 0  \end{matrix}\right] \\
	&= \mathbf{u}_i
 \end{align}$$

>[!lemma]
> If $\mathbf{U}_C = \frac{1}{|S_C^{(k)}|} \sum\limits_{\mathbf{x}^{(k)} \in S_{C}^{(k)}} \mathbf{x}^{(k)}$, then $\sum\limits_{i=1}^K {\mathbf{q}^{(i)}}^T \mathbf{x}^{(i)}$ is an unbiased estimator

>[!pic]
![[qips_lemma.jpg]]


>[!def] Loss Function
> As loss function MSE is used assuming the subspaces are independent and assuming $\mathbf{U}^{(k)}\mathbf{\alpha}_{\mathbf{x}}^{(k)}$ is an unbiased estimator for $\mathbf{x}^{(k)}$ 
> $$ \begin{align}
  \underset{\mathbf{q}\sim Q}{\mathbb{E}}\underset{\mathbf{x}\in X}{\mathbb{E}}\left[\underbrace{\mathbf{q}^T\mathbf{x}}_{=y} - \underbrace{\sum\limits_{k}{\mathbf{q}^{(k)}}^T \underbrace{\mathbf{U}^{(k)}\mathbf{\alpha}_{\mathbf{x}}^{(k)}}_{\approx \mathbf{x}} }_{=\hat{y}}\right] &= \sum\limits_{k}\underset{\mathbf{q}\sim Q}{\mathbb{E}}\underset{\mathbf{x}\in X}{\mathbb{E}}\left[ {\mathbf{q}^{(k)}}^T\left( \mathbf{x}^{(k)} - \mathbf{u}_{\mathbf{x}}^{(k)}\right)\right]^2 \\
  &= \sum\limits_{k}\underbrace{\underset{\mathbf{q}\sim Q}{\mathbb{E}}\mathbf{q}^{(k)}{\mathbf{q}^{(k)}}^T}_{= \mathbf{\Sigma}_{\mathbf{Q}}^{(k)}}\underset{\mathbf{x}\in X}{\mathbb{E}}\left[\left( \mathbf{x}^{(k)} - \mathbf{u}_{\mathbf{x}}^{(k)}\right)\right]^2 \\
  &= \sum\limits_{k} \underset{\mathbf{x}\in X}{\mathbb{E}} \left( \mathbf{x}^{(k)} - \mathbf{u}_{\mathbf{x}}^{(k)}\right)^T\mathbf{\Sigma}_{\mathbf{Q}}^{(k)}\left( \mathbf{x}^{(k)} - \mathbf{u}_{\mathbf{x}}^{(k)}\right)
  \end{align}$$
  The algorithm solves the k-means algorithm in each subspace independently using the Mahalanobis distance based on $\mathbf{\Sigma}_{\mathbf{Q}}^{(k)}$. See [[Mahalabonis Distance]]


>[!algo]
>1. Initialize all $\mathbf{U}^{(k)}$ randomly for all $K$ subspaces
>2. Assign each $\mathbf{x}^{(k)}$ to its closest codebook vector $\mathbf{u}^{(k)}$ according to the Mahalanobis distance 
 $c_{\mathbf{x}}^{(k)} = \underset{c}{\text{argmin}}\left( \mathbf{x}^{(k)} - \mathbf{U}_{c}^{(k)}\right)^T\mathbf{\Sigma}_{\mathbf{Q}}^{(k)}\left( \mathbf{x}^{(k)} - \mathbf{U}_{c}^{(k)}\right)$ 
>3. Update all codebook vectors according to
 $\mathbf{U}_c^{(k)} = \frac{\sum\limits_{\mathbf{x}^{(k)} \in S_{c}^{(k)}} \mathbf{x}^{(k)}}{|S_c^{(k)}|}$ 
>4. Go to 2. until stop-criterion is met

>[!remark]
> If no query vectors are available, the above algorithm is used with $\mathbf{\Sigma}_{\mathbf{Q}} = \mathbf{\Sigma}_{X}$
> If query vectors are available, an adapted version is proposed in the paper 


