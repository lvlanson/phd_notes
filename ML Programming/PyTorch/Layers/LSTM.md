---
aliases: 
- LSTM
- Long Short Term Memory
---
>[!pic]
>![[LSTM_gates.png|600]]


```python
from torch.nn import LSTM
```
>[!initialization]
> ```python
> torch.nn.LSTM(
> 				self, 
> 				input_size, 
> 				hidden_size, 
> 				num_layers=1, 
> 				bias=True, 
> 				batch_first=False, 
> 				dropout=0.0, 
> 				bidirectional=False,  
> 				proj_size=0, 
> 				device=None, 
> 				dtype=None
> 			)
> ```
> #### Arguments
> 
| Argument        | Input Type           |                                                                                                               |
| --------------- | -------------------- | ------------------------------------------------------------------------------------------------------------- |
| `input_size`    | $n \in \mathbb{N}^+$ | dimensionality of each sequence item $\mathbf{x}_t \in \mathbb{R}^{\text{input\_size}}$                       |
| `hidden_size`   | $n \in \mathbb{N}^+$ | dimensionality of hidden states $\mathbf{c}_t, \mathbf{h}_t \in \mathbb{R}^{\text{hidden\_size}}$             |
| `num_layers`    | $n \in \mathbb{N}^+$ | stacking LSTMs `num_layers` times with sequence output of a preceding LSTM is passed into the succeeding LSTM |
| `bias`          | `bool`               | activates or deactivates biases in the linear transformation |
| `batch_first`   | `bool`| changes shape for input,i.e. <ul><li>`True`: $(N,L, H)$</li><li>`False`: $(L,N, H)$</li></ul> with <ul><li>$N$ - batch size</li> <li>$L$ - sequence length</li><li> $H$ - input size</li></ul>|
| `drop_out`      | $p \in [0,1]$ | dropout probability for neurons in unrolled lstm layers|
| `bidirectional` |`bool`| enabling to process input in both directions <br>setting this to true produces as output tuples of states for each direction <ul><li>`True`: outputs will be tuples of `(forward, backward`)</li><li>`False`: outputs will not be tuples</li></ul>|

>[!Usage]
>```python 
>lstm = LSTM(in, hidden, [...])
>lstm(input_seq,(h_0, c_0))  
>```
>lstm returns `out_seq, (h_n, c_n) = lstm(input_seq)`
>
>| Input    |                                                        |
>| --------- | ------------------------------------------------------ |
>| `in` | input sequence |
>| `h_0`     | initial hidden output state of shape|
>| `c_0`     | initial hidden cell state |
>
><br>
>
>| Output    |                                                        |
>| --------- | ------------------------------------------------------ |
>| `out_seq` | sequence of outputs for each element of input sequence |
>| `h_n`     | last hidden output state                               |
>| `c_n`     | last hidden cell state                                 |
>
> Dimensions for `h_i, c_i`
> 
>  | Version                         | Parameter                       |
> | ------------------------------- | ------------------------------- |
> | Unbatched                       | `(D*num_layers, hidden_dim)`    |
> | Batched | `(D*num_layers,N, hidden_dim)` |



 
 
## Examples
>[!example]- Uni-Directional 1-Layer LSTM
>
>```python 
>import torch
>from torch.nn import LSTM 
>
>batch_size = 3
>seq_length = 4
>features   = 5
>hidden_size = 2
>
>some_sequence = torch.rand((batch_size,seq_length,features))
>
>h_0 = torch.zeros(1, batch_size, hidden_size) # 1 is number_layers * bi_directional
>c_0 = torch.zeros(1, batch_size, hidden_size) # 1 is number_layers * bi_directional
>
>lstm = LSTM(input_size=features, 
>			hidden_size=hidden_size,
>			batch_first=True)
>
>out_seq,(h_n, c_n) = lstm(some_sequence, (h_0, c_0))
>
>print(f"Output Sequence:\n{out_seq}\n")
>print(f"Output State:\n{h_n}\n")
>print(f"Hidden State:\n{c_n}\n") 
>```

>[!example]- Bi-Directional 1-Layer LSTM
>
>```python 
>import torch
>from torch.nn import LSTM 
>
>batch_size = 3
>seq_length = 4
>features   = 5
>
>h_0 = torch.zeros(2, batch_size, hidden_size) # 2 is number_layers * bi_directional
>c_0 = torch.zeros(2, batch_size, hidden_size) # 2 is number_layers * bi_directional
>
>some_sequence = torch.rand((batch_size,seq_length,features))
>
>lstm = LSTM(input_size=features, 
>			hidden_size=2,
>			batch_first=True,
>			bidirectional=True)
>
>out_seq,(h_n, c_n) = lstm(some_sequence, (h_0, c_0))
>
>print(f"Output Sequence:\n{out_seq}\n")
>print(f"Output State:\n{h_n}\n")
>print(f"Hidden State:\n{c_n}\n") 
>```