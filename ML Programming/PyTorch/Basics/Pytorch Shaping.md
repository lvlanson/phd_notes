---
aliases:
- shapes
- transpose
- squeeze
- unsqueeze
---

>[!attention]
>Run the code below first for importing necessary libraries!
>```python
>import torch
>```
### Transpose
>[!info]-
>>[!Signature]
>>``` 
>>Tensor.T
>>```
>
>>[!Documentation] 
>>Returns a view of this tensor with its dimensions reversed.
>>
>>If `n` is the number of dimensions in `x`, `x.T` is equivalent to `x.permute(n-1, n-2, ..., 0)`.
>>[Link](https://pytorch.org/docs/stable/tensors.html#torch.Tensor.T)

```python
tensor_1   = torch.rand(size=(3,2))
transposed = tensor_1.T
print(tensor_1.shape)
print(transposed.shape)
```
### Reshape
>[!info]-
>>[!Signature]
>>``` 
>>Tensor.reshape(*shape) → Tensor
>>```
>
>>[!Documentation] 
>>Returns a tensor with the same data and number of elements as `self` but with the specified shape. This method returns a view if `shape` is compatible with the current shape. See `torch.Tensor.view()` on when it is possible to return a view.
>>[Link](https://pytorch.org/docs/stable/tensors.html#torch.Tensor.T)

```python
tensor_1   = torch.rand(size=(3,2))
reshaped   = tensor_1.reshape(1,6)
print(f"{tensor_1.shape=}")
print(f"{tensor_1=}")
print(f"{reshaped.shape=}")
print(f"{reshaped=}")
```

```python
tensor_1   = torch.rand(size=(3,2))
reshaped   = tensor_1.reshape(6)
print(f"{tensor_1.shape=}")
print(f"{tensor_1=}")
print(f"{reshaped.shape=}")
print(f"{reshaped=}")
```

```python
tensor_1   = torch.rand(size=(3,2))
reshaped   = tensor_1.reshape(6,1)
print(f"{tensor_1.shape=}")
print(f"{tensor_1=}")
print(f"{reshaped.shape=}")
print(f"{reshaped=}")
```

### View
>[!info]-
>>[!Signature] 
>>`Tensor.view(*shape) → Tensor`
>
>>[!Documentation]
>>Returns a new tensor with the same data as the self tensor but of a different shape.
>>
>>Own Note: Behaves like reshape but shares the data
>>[More Info!](https://pytorch.org/docs/stable/generated/torch.Tensor.view.html#torch.Tensor.view)

### Stack
>[!info]-
>>[!Signature] 
>>`torch.stack(tensors, dim=0, *, out=None) → Tensor`
>
>>[!Documentation] 
>> Concatenates a sequence of tensors along a new dimension.
>>
>> All tensors need to be of the same size.
stacks input tensors across `dim`
>> [More Info](https://pytorch.org/docs/stable/generated/torch.stack.html)

```python
tensor_1 = torch.tensor([1,2])
stacked = torch.stack([tensor_1, tensor_1, tensor_1], dim=0)
print(stacked)
```

```python
tensor_1 = torch.tensor([1,2])
stacked = torch.stack([tensor_1, tensor_1, tensor_1], dim=1)
print(stacked)
```

### Squeeze
>[!info]-
>>[!Signature] 
>>`torch.squeeze(input, dim=None) → Tensor`
>
>>[!Documentation] 
>> Remove all dimensions with 1 -> `tensor.size([1,1,1,5])` after squeeze `tensor.size([5])`
>> [More Info](https://pytorch.org/docs/stable/generated/torch.squeeze.html#torch.squeeze)

```python
tensor_1 = torch.tensor([[[[1,2,3,4,5]]]])
print(f"{tensor_1.shape=}")
squeezed = tensor_1.squeeze()
print(f"{squeezed.shape=}")
```

### Unsqueeze
>[!info]-
>>[!Signature] 
>>`Tensor.unsqueeze(dim) → Tensor`
>
>>[!Documentation] 
>> Add back a dimension at index `dim`
>> [More Info](https://pytorch.org/docs/stable/generated/torch.unsqueeze.html#torch.unsqueeze)

```python
tensor_1 = torch.tensor([[[[1,2,3,4,5]]]])
print(f"{tensor_1.shape=}")
squeezed = tensor_1.squeeze()
print(f"{squeezed.shape=}")
unsqueezed = squeezed.unsqueeze(0)
print(f"{unsqueezed=}")
print(f"{unsqueezed.shape=}")
```

### Permute
>[!info]-
>>[!Signature] 
>>`Tensor.permute(*dims) → Tensor`
>
>>[!Documentation] 
>> Returns a view of the original tensor input with its dimensions permuted.
>> [More Info](https://pytorch.org/docs/stable/generated/torch.permute.html#torch.permute)


```python
tensor = torch.rand((2,3,1,2))
print(tensor)
tensor = tensor.permute([1,0,3,2])
print(tensor.shape)
```