---
aliases:
- pytorch layers
---
>[!attention]
>Run the code below first for importing necessary libraries!
>```python
>import torch
>```

### Linear
>[!info]-
>>[!Signature] 
>> `torch.nn.Linear(in_features, out_features, bias=True, device=None, dtype=None)`
>
>>[!Documentation]
>> Applies a linear transformation to the incoming data: 
>> $$ \underbrace{\mathbf{y}}_{\text{Output}} = \underbrace{\mathbf{x}}_{\text{Input}} \;\; \underbrace{A^T + b}_{\text{Linear Layer}} $$
>> [Documentation](https://pytorch.org/docs/stable/generated/torch.nn.Linear.html#torch.nn.Linear)


```python
x = torch.tensor([1, 2], dtype=torch.float32)

# Setting seed for reproducibility
torch.manual_seed(42)
# This uses matrix multiplication
linear = torch.nn.Linear(in_features=2, # inner dimension of input 
                         out_features=6) # outer dimension for output 
output = linear(x)
print(f"Input shape: {x.shape}\n")
print(f"Output:\n{output}\n\nOutput shape: {output.shape}")
```