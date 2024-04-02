>[!note] Note 1
> Solutions of linear homogeneous systems of equations are usually given in the form \[[[../../PhD Studies/Mathematic Basics/Ordinary Differential Equations/5 - Systems of Linear  Differential Equations#^abe58b|1]]]
> $$\mathbf{x}_{gen}(t)= c_{1}e^{\lambda_{1}t}\mathbf{v}^{(1)}+\dots+c_{n}e^{\lambda_{n}t}\mathbf{v}^{(n)}$$
> The plan is to use Fourier series, which are a series of trigonometric functions ($\sin, \cos$) \[[[../../PhD Studies/Mathematic Basics/Fourier Analysis/1 -  Fourier Series (OLD)#^da9999|2]]]
> $$\hat{f}(t) = \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos(kt)+b_{k} \sin(kt)$$
> Note, that any Fourier series can be also represented in [[../../PhD Studies/Mathematic Basics/Complex Analysis/Fundamental Properties#^88d84a|Euler form]]of complex numbers coefficients \[[[../../PDFs/howell2016.pdf#page=157|howell2016]]]
> $$FS[f]\vert_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i2\pi \omega_{k}t}$$
> which could solve the representation issue.
> 
> I was wondering how to connect a sine/cosine representation to an exponential representation which the solution of the homogeneous system would yield.

>[!note] Note 2
>By construction the equations are [[../../PhD Studies/Mathematic Basics/Ordinary Differential Equations/5 - Systems of Linear  Differential Equations#^abe58b|decoupled]], therefore we can solve the system of equations using the [[../../PhD Studies/Mathematic Basics/Linear Algebra/Eigenvectors and Eigenvalues#^a0a687|diagonalization method ]] by having eigenvalues and eigenvectors.


