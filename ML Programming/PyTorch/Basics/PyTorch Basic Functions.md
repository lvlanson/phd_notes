---
aliases:
- Basic Functions
---
>[!attention]
>Run the code below first for importing necessary libraries!
>```python
>import torch
>```
### Aggregation Functions

```python
print(f"Minimum: {x.min()}")
print(f"Maximum: {x.max()}")
# print(f"Mean: {x.mean()}") # this will error
print(f"Mean: {x.type(torch.float32).mean()}") # won't work without float datatype
print(f"Sum: {x.sum()}")

# Returns index of max and min values
print(f"Index where max value occurs: {x.argmax()}")
print(f"Index where min value occurs: {x.argmin()}")
```

>[!info]-
> `torch.min(input) → Tensor` [Doc](https://pytorch.org/docs/stable/generated/torch.min.html#torch.min)
> `torch.max(input) → Tensor` [Doc](https://pytorch.org/docs/stable/generated/torch.max.html)
> `torch.mean(input, *, dtype=None) → Tensor` [Doc](https://pytorch.org/docs/stable/generated/torch.mean.html#torch.mean)
> `torch.sum(input, *, dtype=None) → Tensor` [Doc](https://pytorch.org/docs/stable/generated/torch.sum.html#torch.sum)
> `torch.argmax(input) → LongTensor` [Doc](https://pytorch.org/docs/stable/generated/torch.sum.html#torch.sum)
> `torch.argmin(input, dim=None, keepdim=False) → LongTensor` [Doc](https://pytorch.org/docs/stable/generated/torch.argmin.html#torch.argmin)

### Random Tensor
>[!info]-
>>[!Signature] 
>> `torch.randn(*size, *, generator=None, out=None, dtype=None, layout=torch.strided, device=None, requires_grad=False, pin_memory=False) → Tensor`
>
>>[!Documentation]
>> Returns a tensor filled with random numbers from a normal distribution with mean $0$ and variance $1$ (also called the standard normal distribution).
>> The shape of the tensor is defined by the variable argument `size`.
>> [Documentation](https://pytorch.org/docs/stable/generated/torch.randn.html)

```python
print(torch.randn(4))
print(torch.randn(2, 3))
```