>[!note] Note 1
> Solutions of linear homogeneous systems of equations are usually given in the form \[[[../../PhD Studies/Mathematic Basics/Ordinary Differential Equations/5 - Systems of Linear  Differential Equations#^abe58b|1]]]
> $$\mathbf{x}_{gen}(t)= c_{1}e^{\lambda_{1}t}\mathbf{v}^{(1)}+\dots+c_{n}e^{\lambda_{n}t}\mathbf{v}^{(n)}$$
> The plan is to use Fourier series, which are a series of trigonometric functions ($\sin, \cos$) \[[[../../PhD Studies/Mathematic Basics/Fourier Analysis/1 - Fourier Series (OLD)#^da9999|2]]]
> $$\hat{f}(t) = \frac{a_{0}}{2} + \sum_{k=1}^\infty a_{k} \cos(kt)+b_{k} \sin(kt)$$
> Note, that any Fourier series can be also represented in [[../../PhD Studies/Mathematic Basics/Complex Analysis/Fundamental Properties#^88d84a|Euler form]]of complex numbers coefficients \[[[../../PDFs/howell2016.pdf#page=157|howell2016]]]
> $$FS[f]\vert_{t}= \sum_{k=-\infty}^\infty c_{k}e^{i2\pi \omega_{k}t}$$
> which could solve the representation issue.
> 
> I was wondering how to connect a sine/cosine representation to an exponential representation which the solution of the homogeneous system would yield.

>[!note] Note 2
>By construction the equations are [[../../PhD Studies/Mathematic Basics/Ordinary Differential Equations/5 - Systems of Linear  Differential Equations#^abe58b|decoupled]], therefore we can solve the system of equations using the [[../../PhD Studies/Mathematic Basics/Linear Algebra/Eigenvectors and Eigenvalues#^a0a687|diagonalization method ]] by having eigenvalues and eigenvectors.

>[!note] Note 3
>We will construct using [[../../PhD Studies/Mathematic Basics/Fourier Analysis/8 - Discrete Fourier Transform and Trigonometric Interpolation|Discrete Fourier Transform and Trigonometric Interpolation]] in [[../../PhD Studies/Mathematic Basics/Fourier Analysis/8 - Discrete Fourier Transform and Trigonometric Interpolation#^ddb0ce|Euler's form]], i.e. for $\mathbf{x} \in \mathbb{R}^{n}$ we have for some undetermined $X$
>>If $n$ is odd:
>>$$q(X) = \sum_{j=-K}^K c_{j} \exp(2\pi i j X)$$ 
>>If $n$ is even:
>>$$\begin{align}
>>q(X) &=\frac{c_{k}}{2}(\exp(2\pi iKX) +\exp(-2\pi iKX)) + \sum_{j=-K+1}^{K-1} c_{j} \exp(2\pi ijX)  \\
>> &= \sum_{j=-K+1}^{K}c_{j}\exp(2\pi ijX)
>>\end{align}$$
>
>with $K=\left\lceil  \frac{n}{2}  \right\rceil$ and where the interpolants $c_{j}$ can be determined with $x_{l}\in \mathbf{x}$
>$$c_{j} = \frac{1}{n}\sum_{l=0}^{n-1} x_{l} \exp(-2\pi i j x_{l})\tag*{$j \in \{ 0,\dots,n-1 \}$}$$
>Hence, we yield a polynomial of the form
>$$q(X)=\sum_{j=-K}^K a_{j}\exp(2\pi ijX)$$
>where the $a_{j}\in \mathbb{C}$ are in accordance to the above described system.

>[!note] Note 4 Constructing the System
>- **<span style="color:#3884ff">Preparation:</span>** 
>The trigonometric polynomial should be of the form for $\mathbf{x} \in \mathbb{R}^n$
>$$q(X)=\sum_{j=-K}^K a_{j}\exp(2\pi ijX)$$
>with $a_{j} \in \mathbb{C}$
>
>- **<span style="color:#3884ff">Determining the Differential Equation:</span>**
>$$\begin{align}
> \frac{dq}{dX}&= \sum_{j=-K}^K (2\pi ij )a_{j}\exp(2\pi ijX) \\
> &= 2\pi ij \sum_{j=-K}^K a_{j}\exp(2\pi ijX)
>\end{align}$$
>
>- **<span style="color:#3884ff">Building a system of equations of degree $d>0$.</span>**
>We have to select $d$ frequencies of interest. The **<span style="color:#3884ff">frequencies holding the most discriminatory information</span>** should be selected. 
>>**<span style="color:#f7b8ff">Questions: </span>**
>>- Selection with variance over the Fourier Transforms?
>>- Do we need to remove frequencies to get a quadratic matrix?
