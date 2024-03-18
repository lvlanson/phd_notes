>[!note]
>A nice resource on this topic is [[../../../PDFs/hall2015.pdf|Lie Groups, Lie Algebras, and Representations by Brian C. Hall]]

>[!terminology]
>- [[#^df6259|Matrix Exponential]]
>- [[#^3c5427|Jordan Normalform]]

## A.1 The Matrix Exponential

>[!def] Definition Matrix Exponential ([[../../../PDFs/nagy.pdf#page=385|Source 1]], [[../../../PDFs/hall2015.pdf#page=43|Source 2]])
>The **exponential** of a square matrix $A$ is the [[Series#^588b80|power series]] centered at $x=0$
>---
>$$e^A = \sum_{n=0}^\infty \frac{A^n}{n!}$$
>
>---
>with $$A^0=I$$
>being the identity matrix.
>>[!remark]
>>This definition follows the general [[../Calculus/Series#^9251bc|definition of the exponential function]].

^df6259

>[!theorem] Theorem Convergence of the Matrix Exponential ([[../../../PDFs/nagy.pdf#page=385|Source 1]], [[../../../PDFs/hall2015.pdf#page=43|Source 2]])
>The power series of the [[#^df6259|matrix exponential]] converges for all $n \times n$ matrices
>>[!proof]-
>>We need some additional definition the proof the theorem
>>>[!def] Definition Hilbert-Schmidt Norm/Frobenius Norm
>>>For any $n \times n$ matrix $A$ we define the norm
>>>$$\lvert\lvert A \rvert\rvert = \left(\sum_{j,k=1}^n \lvert X_{jk} \rvert^2 \right)^{1/2} $$
>>>>[!remark]
>>>>Note the following properties hold $n \times n$ matrices $A,B$ for the Hilbert Schmidt Norm
>>>>1. $\lvert\lvert AB \rvert\rvert \leq \lvert\lvert A \rvert\rvert\;\lvert\lvert B \rvert\rvert$ <div align="right">(Submultiplicative Property)</div>
>>>>2. $\lvert\lvert A + B \rvert\rvert \leq \lvert\lvert A \rvert\rvert + \lvert\lvert B \rvert\rvert$ <div align="right">(Triangle Inequality)</div>
>>
>>Now, taking the norm on matrices of the sum yields
>>$$\sum_{m=0}^\infty \left\lvert \left\lvert  \frac{A^m}{m!}  \right\rvert \right\rvert \leq \lvert\lvert I \rvert\rvert + \sum_{m=1}^\infty \frac{\lvert\lvert A \rvert\rvert^m}{m!} < \infty   $$
>>>[!note]
>>>We use the property, that the norm of a matrix is less than infinity, because it inherits this property from the norm. Then we used the properties of the norm and the submultiplicativity.

>[!theorem] Theorem Exponential of Diagonal Matrix ([[../../../PDFs/nagy.pdf#page=385|Source]])
>If $D=\mathrm{diag}\left(d_{1}, \dots, d_{n}\right)$, then
>---
>$$e^D = \mathrm{diag}\left(e^{d_{1}}, \dots, e^{d_{n}}\right)$$
>
>---
>>[!proof]-
>>We start with the [[#^df6259| definition of the matrix exponential]] 
>>$$\begin{align}
>> e^D &= \sum_{i=0}^\infty \frac{1}{k!} \Big(\mathrm{diag}\left(d_{1}, \dots, d_{n}\right)\Big)^k \tag{$D$ diagonal}\\
>> &= \sum_{i=0}^\infty \frac{1}{k!} \mathrm{diag}\left(d_{1}^k, \dots, d_{n}^k\right) \\ 
>> &= \sum_{i=0}^\infty \mathrm{diag}\left(\frac{d_{1}^k}{k!}, \dots, \frac{d_{n}^k}{k!}\right) \\ 
>> &= \mathrm{diag}\left(\sum_{i=0}^\infty \frac{d_{1}^k}{k!}, \dots,\sum_{i=0}^\infty  \frac{d_{n}^k}{k!}\right) \tag{Definition Exponential}\\ 
>> &= \mathrm{diag}\left(e^{d_{1}^k}, \dots,e^{d_{n}^k}\right) \\ 
>>\end{align}$$
>>$$\tag*{$\square$}$$

^5c6d39

## A.2 Diagonalization Matrix Formulae

>[!Theorem] Theorem Powers of Diagonalizable Matrices ([[../../../PDFs/nagy.pdf#page=386|Source]])
>If an $n \times n$ matrix $A$ is diagonalizable, with invertible matrix $P$ and diagonal matrix $D$ satisfying $A = PDP^{-1}$, then for every integer $k \geq 1$ holds
>---
>$$A^k = PD^kP^{-1}$$
>
>---
>>[!proof]-
>>First we note, that any [[../Linear Algebra/Eigenvectors and Eigenvalues#^3b9ec0|diagonalizable matrix]] can be given as 
>>$$A=PDP^{-1}$$
>>with $P$ being a non-singular matrix. Further we note
>>$$D^k = \mathrm{diag}\left(d_{1}^k, \dots d_{n}^k\right)$$
>>We will use induction to prove the identity
>>>Base Case $k=1$
>>
>>This can easily be verified by 
>>$$A=PDP^{-1}$$
>><div align="right"> :luc_check:</div>
>>
>>> Base Case k=2
>>
>>This also can be easily shown as
>>$$\begin{align}
>> A^2 &= \Big(PDP^{-1}\Big)^2 \\
>> &= PD\underbrace{ P^{-1}P }_{ =I }DP \\
>> &= PD^2P
>>\end{align}$$
>><div align="right"> :luc_check:</div>
>>
>>>Induction Step $k \mapsto k+1$
>>
>>$$\begin{align}
>> A^{k+1} &= \Big(PDP^{-1}\Big)^{k+1}  \\
>> &= \underbrace{ \Big(PDP^{-1}\Big)^k }_{ =PD^kP^{-1} } PDP^{-1} \\
>> &= PD^k\underbrace{ P^{-1} P }_{ =I }DP^{-1} \\ 
>> &=PD^{k+1}P^{-1}
>>\end{align}$$
>>Which concludes the proof $$\tag*{$\square$}$$
>
>>[!remark]
>>A diagonalized matrix is also called **Jordan Normalform**

^3c5427

>[!theorem] Theorem Exponential of Diagonalizable Matrices ([[../../../PDFs/nagy.pdf#page=386|Source]])
> If an $n \times n$ matrix $A$ is diagonalizable, with invertible matrix $P$ and diagonal matrix $D$ satisfying $A=PDP^{-1}$, then the exponential of matrix $A$ is given by
> ---
> $$e^A = Pe^{D}P^{-1}$$
>
>---
>>[!remark]- Remark on Eigenvectors and Eigenvalues
>>We know that by the [[../Linear Algebra/Eigenvectors and Eigenvalues#^a0a687| diagonalization theorem I]] for eigenvector $\mathbf{x}_{i}$ and corresponding eigenvalues $\lambda_{i}$ for matrix $A$, we have the relation
>>$$A\mathbf{x}_{i}= \lambda_{i}\mathbf{x}_{i}$$
>>Now, we denote $X = \left[\mathbf{x}_{1}, \dots, \mathbf{x}_{n}\right]$ and $D=\begin{bmatrix}\lambda_{1} & \dots & 0 \\ \vdots & \ddots & \vdots \\ 0 &\dots & \lambda_{n}\end{bmatrix}$ and have the identity
>>$$\begin{align}
>> AX &= XD \qquad&&\Big\vert \cdot X^{-1} \\
>> A &= XDX^{-1}
>>\end{align}$$
>>where $D$ is the diagonal matrix of eigenvalues and $X$ the matrix of eigenvectors.
>
>>[!proof]-
>>We use the definitions accordingly
>>$$\begin{align}
>> e^A &= \sum_{k=0}^\infty \frac{1}{k!}A^k \tag{Diagonalization} \\
>> &= \sum_{k=0}^\infty \frac{1}{k!}(PDP^{-1})^k \tag{Powers of Diag Matrices} \\
>> &= \sum_{k=0}^\infty \frac{1}{k!}(PD^kP^{-1}) \tag{Linearity} \\
>> &= P \left( \sum_{k=0}^\infty \frac{1}{k!}D^k \right) P^{-1} \tag{Matrix Exponential} \\
>> &= Pe^{D}P^{-1} 
>>\end{align}$$
>>$$\tag*{$\square$}$$
>
>>[!property]
>>The preceding theorems are of concern with respect to exponential function of
>>$$\exp: \mathbb{R}^{n \times n} \to \mathbb{R}^{n\times n}$$
>>If we want to solve systems of linear ODEs, we actually have
>>$$f: \mathbb{R} \to \mathbb{R}^{n \times n}$$
>>because our dependent variable is $t$ and the matrix $A$ is fixed. Therefore, we make the following adaption
>>----
>>$$e^{At} = Pe^{Dt}P^{-1}$$
>>
>>---
>
>>[!example] 
>>Compute $e^{At}$ with $A = \begin{bmatrix}1 & 3 \\ 3 & 1\end{bmatrix}$ and $t \in \mathbb{R}$
>>>[!example]- Solution
>>>First we compute the eigenvectors and eigenvalues, since they allow us to easily construct the necessary components. We have to solve
>>>$$A\mathbf{x}= \lambda \mathbf{x}$$
>>> which can be solved using characteristic polynomial derived from [[../Linear Algebra/Eigenvectors and Eigenvalues#^a70a98| given identity]]
>>> $$\det(A-\lambda I)=0 \tag{1}$$
>>> We get
>>> $$\begin{align}
>>> \begin{vmatrix}
>>> 1 -\lambda & 3 \\
>>> 3 & 1-\lambda
>>>\end{vmatrix} &= 0 \\
>>> (1- \lambda)^2 - 9 &= 0  \\
>>>\end{align}$$
>>>This characteristical polynomial can easily be solved with
>>>$$\begin{align}
>>> \lambda_{1} &= 4 \\
>>> \lambda_{2} & = -2
>>>\end{align}$$
>>> Solving equation $(1)$ with each of the eigenvalues yields the eigenvectors
>>> $$\begin{align}
>>> \mathbf{x}_{1} &= [1,1]^T\\
>>> \mathbf{x}_{2} &= [-1, 1]^T
>>>\end{align}$$
>>>By the remark we can construct $P$ by the eigenvectors and $D$ by the corresponding eigenvalues. We state
>>>$$\begin{alignat}{2}
>>> P &= [\mathbf{x}_{1}, \mathbf{x}_{2}] &&= \begin{bmatrix}
>>> 1& -1  \\
>>> 1& 1
>>>\end{bmatrix} \\
>>> D &= \begin{bmatrix}
>>> \lambda_{1} & 0 \\
>>> 0 & \lambda_{2}
>>>\end{bmatrix} &&=\begin{bmatrix}
>>> 4 & 0 \\
>>> 0 & -2
>>>\end{bmatrix}
>>>\end{alignat}$$
>>>Finally, we need to compute the inverse of $P$
>>>$$\begin{align}
>>> P^{-1} &= \frac{1}{2}\begin{bmatrix}
>>> 1& 1  \\
>>> -1& 1
>>>\end{bmatrix}
>>>\end{align}$$
>>>The exponential function $e^{At}$ can therefore be given as
>>>$$\begin{align}
>>> e^{At} &= Pe^{Dt}P^{-1} \\
>>>  &= \begin{bmatrix}
>>> 1& -1  \\
>>> 1& 1
>>>\end{bmatrix} \begin{bmatrix}
>>> e^{4t} & 0 \\
>>> 0 & e^{-2t}
>>>\end{bmatrix}\frac{1}{2}\begin{bmatrix}
>>> 1& 1  \\
>>> -1& 1
>>>\end{bmatrix}
>>>\end{align}$$

^56ae16

## A.3 Properties of the Exponential

>[!theorem] Theorem Algebraic Properties ([[../../../PDFs/nagy.pdf#page=387|Source]])
>1. If $A= \begin{bmatrix} 0 & \dots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \dots & 0\end{bmatrix} \implies e^{A}= I$ 
>2. $(e^{A})^T = e^{(A^T)}$ with $T$ being the transposed
>3. $k \geq 0: A^ke^A = e^A A^k$
>4. If $AB=BA \implies Ae^B=e^BA$ and $e^Ae^B = e^Be^A$
>
>>[!remark]
>>The exponential for real numbers $a,b$ satisfies
>>$$e^a e^b = a^{a+b}$$
>>but the matrix exponential does not generally satisfy
>>$$e^Ae^B \neq e^{A+B}$$

^6ed8d5

>[!theorem] Theorem Commutative Group Property
>If $A$ is an $n \times n$ matrix and $s,t \in \mathbb{R}$, then
>---
>$$e^{As}e^{At} = e^{A(s+t)}$$
>
>---
>>[!property] Properties
>> 1. Associativity: $t,s,r \in \mathbb{R}:$
>>  $$\left(e^{At}e^{As}\right)e^{Ar} = e^{At}\left(e^{As}e^{Ar}\right)$$
>> 2. Neutral Element: $t=0$ 
>> $$e^{A \cdot 0} = e^{\mathbb{0}} = 1$$
>> 3. Inverse Element: $t, -t \in \mathbb{R}$
>> $$e^{At}e^{-At}= e^{A(t-t)} = e^{\mathbb{0}}=1$$
>> 4. Commutativity: $t,s \in \mathbb{R}$
>> $$e^{At}e^{As}=e^{As}e^{At}$$
>
>>[!proof]-
>>We use the definition
>>$$\begin{align}
>>e^{As}e^{At} &= \left( \sum_{j=0}^{\infty}\frac{A^js^j}{j!} \right)\left( \sum_{k=0}^{\infty}\frac{A^kt^k}{k!} \right) \\
>> &=\sum_{j=0}^{\infty}\sum_{k=0}^{\infty}\frac{A^js^jA^kt^k}{j!k!}    \\
>> &=\sum_{j=0}^{\infty}\sum_{k=0}^{\infty}\frac{A^{j+k}s^jt^k}{j!k!}    \\
>>\end{align}$$
>>We make a change of variables, denote
>>$$\begin{align}
>> n &= j + k \\
>> j &= n-k
>>\end{align}$$
>>and we get
>>$$\begin{align}
>> \phantom{e^{As}e^{At}} &= \sum_{n=0}^{\infty}\sum_{k=0}^{n}\frac{A^{n}s^{n-k}t^k}{(n-k)!k!} \\
>> \phantom{e^{As}e^{At}} &= \sum_{n=0}^{\infty}\sum_{k=0}^{n}\frac{A^{n} n!}{n!(n-k)!k!}s^{n-k}t^k \\
>> \phantom{e^{As}e^{At}} &= \sum_{n=0}^{\infty}\sum_{k=0}^{n}\frac{A^{n}}{n!}\frac{A^n!}{(n-k)!k!}s^{n-k}t^k \\
>> \phantom{e^{As}e^{At}} &= \sum_{n=0}^{\infty}\frac{A^{n}}{n!}\sum_{k=0}^{n}\frac{A^n!}{(n-k)!k!}s^{n-k}t^k \\
>>\end{align}$$
>>>[!note]- Comment on Range Change of Sums
>>>1. **Original Summation Bounds**
>>>In the original double sum $j$ ranges from $0$ to $\infty$ and $k$ ranges from $0$ to $\infty$. This means that every pair of $j$ and $k$ values is considered, resulting in every possible combination of terms $\frac{A^{j+k}s^jt^k}{j!k!}$<br><br>
>>>2. **New Index Relationship**
>>>After the change of variables, the new index $n = j+k$ represents the total number of iterations in the sum. The value of $k$ is still bounded by $0$ and $n$, ensuring that $j=n-k$ remains non-negative. <br><br>
>>>3. **Non-Duplication**
>>>Because $n$ and $k$ are related through $n=j+k$ each value of $n$ corresponds to a unique combination of $j$ and $k$. Specifically, for each fixed $n,k$ ranges from $0$ to $n$, and the corresponding $j$ values are uniquely determined by $j=n-k$<br><br>
>>>4. **Summation Over Non-Duplicate Terms:**
>>>As result, the double sum over $n$ and $k$ ensures that each term $\frac{A^nn!}{(n!)(n-k)!k!}s^{n-k}t^k$ is included exactly once in the summation, covering all possible combinations of $j$ and $k$ without duplication
>>
>>We use the definition of the binomial
>>$$(s+t)^n = \sum_{k=0}^n \frac{n!}{(n-k)!k!}s^{n-k}t^k$$
>>Inserting this we get
>>$$\begin{align}
>> \phantom{e^{As}e^{At}} &= \sum_{n=0}^{\infty}\frac{A^{n}}{n!}(s+t)^n\\
>> \phantom{e^{As}e^{At}} &= \sum_{n=0}^{\infty}\frac{A^{n}(s+t)^n}{n!}\\
>> &= e^{A(s+t)} \tag*{$\square$}
>>\end{align}$$

^cd67f1

>[!theorem] Theorem Derivative of the Exponential ([[../../../PDFs/nagy.pdf#page=389|Source]])
>If $A$ is an $n \times n$ matrix, and $t \in \mathbb{R}$, then
>---
>$$\frac{d}{dt}e^{At} = Ae^{At}= e^{At}A$$
>
>---
>>[!proof]-
>>We use the definition of the [[#^df6259|matrix exponential]]
>>$$\begin{align}
>> \frac{d}{dt}e^{At} &= \frac{d}{dt}\sum_{n=0}^\infty \frac{A^nt^n}{n!}\\
>>  &= \sum_{n=0}^\infty \frac{A^n}{n!}\frac{d}{dt}t^n \\
>>  &= \sum_{n=0}^\infty \frac{A^n}{n!}nt^{n-1} \\
>>  &= \sum_{n=1}^\infty \frac{A^nt^{n-1}}{(n-1)!} \tag{$n=0$ not defined}\\
>>  &= A\sum_{n=1}^\infty \frac{A^{n-1}t^{n-1}}{(n-1)!} \\ 
>>  &= A\sum_{m=0}^\infty \frac{A^{m}t^{m}}{m!} \tag{$m=n-1$}\\ 
>>  &= Ae^{At}
>>\end{align}$$

^730bfa

>[!theorem] Theorem Exponent Rule ([[../../../PDFs/nagy.pdf#page=390|Source]])
>If $A,B$ are $n \times n$ matrices, such that $AB=BA$, then 
>$$e^{A+B}= e^Ae^B$$
>>[!proof]-
>>Let $$F(t)=e^{(A+B)t}e^{-Bt}e^{-At}$$
>>>[!note]- Strategy
>>>We want to show that this function 
>>>$$F(t)= I$$
>>>for any $t \in \mathbb{R}$. If we are able to show this, we can conclude
>>>$$\begin{align}
>>> F(t)&= e^{(A+B)t} e^{-Bt}e^{-At} \\
>>> &= e^{(A+B)t} e^{-(A+B)t} \\
>>> &= e^{(A-A+B-B)t} \\
>>> &= e^{\mathbb{0}} \\
>>> &= I \\
>>>\end{align}$$
>>
>> We compute the derivative $F'(t)$ using the product rule and the [[#^730bfa| derivative of the exponential]]
>> $$\begin{align}
>> F'(t) = \;\;\;\;&(A+B)e^{(A+B)t}e^{-Bt}e^{-At}   \\
>>       + \;&e^{(A+B)t}(-B)e^{-Bt}e^{-At}   \\
>>       + \;&e^{(A+B)t}e^{-Bt}(-A)e^{-At} 
>>\end{align}$$
>>Note, by the [[#^6ed8d5| 4th algebraic property]] we have
>>$$AB=BA \quad \Longrightarrow \quad e^{-Bt}A = Ae^{-Bt}$$
>>therefore we can arrange
>>$$\begin{align}
>> F'(t) = \;\;\;\;&(A+B)e^{(A+B)t}e^{-Bt}e^{-At}   \\
>>       - \;&e^{(A+B)t}Be^{-Bt}e^{-At}   \\
>>       - \;&e^{(A+B)t}Ae^{-Bt}e^{-At} 
>>\end{align}$$
>>Further, we use the same property on the identity
>>$$(A+B)B = B(A+B) \quad \Longrightarrow \quad e^{(A+B)t}B = Be^{(A+B)t}$$
>>$$\begin{align}
>> F'(t) = \;\;\;\;&(A+B)\underbrace{ e^{(A+B)t}e^{-Bt}e^{-At} }_{ =F(t) }   \\
>>       - \;&B\underbrace{ e^{(A+B)t}e^{-Bt}e^{-At} }_{ =F(t) }   \\
>>       - \;&A\underbrace{ e^{(A+B)t}e^{-Bt}e^{-At} }_{ =F(t) } \\
>>\end{align}$$
>>Substituting yields
>>$$\begin{align}
>> F'(t) &= (A+B)F(t)-AF(t)-BF(t) \\
>>       &= F(t)\big(A+B-A-B\big) \\
>>       &= 0
>>\end{align}$$
>>Hence, $F(t)$ must be a constant function. To guarantee F(t) being constant, we have $t=0$, which yields
>>$$F(t)=F(0)=I$$
>>Concluding
>>$$e^{(A+B)t}e^{-Bt}e^{-At} = I \quad \Longrightarrow \quad e^{A+B}= e^Ae^B \tag*{$\square$}$$