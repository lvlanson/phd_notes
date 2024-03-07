>[!Source]
><u>Book:</u> Maximum Likelihood Estimation and Inference: With Examples in R, SAS and ADMB
>>URL: https://www.wiley.com/en-us/Maximum+Likelihood+Estimation+and+Inference%3A+With+Examples+in+R%2C+SAS+and+ADMB-p-9780470094822
>PDF: [PDF](../../../../PDFs/millar2011.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@millar2011)
>
><u>Book:</u> Econometric Analysis (Page 537)
>>URL: https://elibrary.pearson.de/book/99.150005/9781292231150
>PDF: [PDF](../../../../PDFs/greene2019.pdf)
>Zotero: [Zotero-Link](zotero://select/items/@greene2019)


>[!notation]
| Parameter                     | Meaning                  |
| ----------------------------- | ------------------------ |
| $\mathbf{x}=(x_i)_{i=1}^n$    | $n$ observations         |
| $\mathbf{\eta}$               | distribution parameters as scalar or vector  |
| $f(\mathbf{y};\mathbf{\eta})$ | (joint) density function |
| $X,Y$                         | Random Variables                         |


>[!def] Parameterics Statistical Model
> A parametric statistical model is a collection of joint density functions, $f(\mathbf{x}; \mathbf{\eta})$ with $\eta$ being the models parameters
> 

>[!example]- Example Normal Model
>-> Normal Distribution: $N(\mu, \sigma^2)$
>	-> Collection of all possible normal distributions (_Y is normally distributed_)
>-> parameter value: $\mathbf{\eta} = (\mu, \sigma)$

>[!def] Definition Likelihood Function
>The likelihood function is the (joint) density function evaluated at the observed data, and regarded as a function of $\eta$ alone. That is
>$$ \begin{align} L(\eta) \equiv L(\eta; \mathbf{x}) &= f(\mathbf{x}; \mathbf{\eta}) \\
>													&=\prod_{i=1}^n f(x_i ; \eta)\end{align}$$


>[!def] Definition Log Likelihood
> Let $L$ be a _likelihood function_, the log-likelihood function is given as $$\text{ln }(L)$$
>>[!note]
>>The (natural) logarithm provides useful properties when calculating the derivatives. Since maximizing $L$ and maximizing ln$(L)$ is equivalent due to the fact of the natural logarithm being monotonically increasing, it is preferred to optimize over ln$(L)$.
>>Further, products in the likelihood function $L$ turn into sums, which in the derivative with respect to the optimization parameter can turn to $0$ if they are independent from it.

>[!def] Definition Maximum Likelihood Estimate (MLE)
>Given observations $\mathbf{x}$ and parameters $\eta$ that maximize $L(\eta)$ over the parameter space is called a maximum likelihood estimate (MLE) of the unknown true parameter $\eta$.


>[!example]
>Consider a random sample of 10 observations from a Poisson distribution
>$$ \mathbf{x} = (5, 0, 1, 1, 0, 3, 2, 3, 4, 1) $$
>The probability density function of the Poisson distribution is given as
>$$ f(x_i ; \eta) = \frac{e^{-\eta}\eta^{x_i}}{x_i!}$$
>
>>**<u>Task:</u> Find the optimal parameter $\eta$ which maximizes the probability density funtion $f$**
>
> We use the natural logarithm on the probability density function to finde the **Maximum Likelihood Estimate**
> $$\begin{align}
> 	\ln L(\eta ; \mathbf{x}) &= \ln \left(\prod_{i=1}^n\frac{e^{-\eta}\eta^{x_i}}{x_i!}\right) \\
> 							 &= \sum_{i=1}^n\ln \left(e^{-\eta}\right) + \left(\eta^{x_i}\right) - \left(x_i!\right) \\
> 							 &= -n\eta + \ln \eta \sum_{i=1}^n x_i \sum_{i=1}^n \left(\ln{x_i!}\right)\
> \end{align}$$
> Inserting the values from the observations gives
> $$\ln L(\eta ; \mathbf{x}) = -10\eta + 20 \ln \eta - 12\,242 $$
> Now calculating the derivative with respect to the optimization parameter $\eta$ gives
> $$\begin{align}
> 	\frac{\text{d} \ln L(\eta ; \mathbf{x})}{\text{d} \eta} &= -10 + \frac{20}{\eta} \\
> \end{align}$$
> Setting the derivative $\frac{\text{d} \ln L(\eta ; \mathbf{x})}{\text{d} \eta} = 0$ solves for the extremum, hence
> $$\begin{align}
> 	0 &= -10 + \frac{20}{\eta} \\
> 	\eta &= 2
> \end{align}$$
> 
> Checking the second derivative tells us, that we have found a maximum
> $$\begin{align}
> 	\frac{\text{d}^2 \ln L(\eta ; \mathbf{x})}{\text{d} \eta^2} &= \frac{-20}{\eta^2} < 0 \\
> \end{align}$$

