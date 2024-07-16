>[!algo] Architecture sLSTM ([[../../../PDFs/beck2024.pdf|Source]])
> Denote at time $t$ for input $\mathbf{x} \in \mathbf{R}^n$ with LSTM hidden dimensionality $1$
> 
>| States                     | Gates                 | Weights |
>| -------------------------- | --------------------- | ------- |
>| $c_t \in \mathbb{R}$ - cell state         | $z_{t}\in \mathbb{R}$ - cell input  | $\mathbf{w}_{z,i,f,o}\in \mathbb{R}^n$ - input weights for respective gates        |
>| $h_{t}\in \mathbb{R}$ - hidden state     | $f_{t}\in \mathbb{R}$ - forget gate |  $r_{z,i,f,o}\in \mathbb{R}$ - cell weights for respective gates       |
>| $n_{t}\in \mathbb{R}$ - normalizer state | $i_{t}\in \mathbb{R}$ - input gate  |  $b_{z,i,f,o}\in \mathbb{R}$ - biases for respective gates       |
>| $m_{t}\in \mathbb{R}$ - stabilizer state | $o_{t}\in \mathbb{R}$ - output gate |  $\phi$ - activation function, usually $\tanh$       |
> 
> ![[Figures/sLSTM_raw.png]]
>>[!note]- Note on Hidden Dimensionality
>>If the hidden dimensionality $d$ is greater than $1$ all scalars turn into vectors and the input weight $\mathbf{w}$ becomes a matrix $\mathbf{W} \in \mathbb{R}^{n \times d}$ and the cell weight becomes a matrix too $\mathbf{R} \in \mathbb{R}^{n \times d}$.
>
>>[!note] Note: exponential function is used as activation function
>
>>[!danger] The exponential function can blow up, stabilization and normalization is needed!
>
>![[Figures/sLSTM_stabilized.png]]
