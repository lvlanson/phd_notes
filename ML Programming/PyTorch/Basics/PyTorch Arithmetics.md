---
aliases:
- pytorch arithmetic
---
>[!attention]
>Run the code below first for importing necessary libraries!
>```python
>import torch
>```
### Add by some scalar (+ and -)
>[!info]-
>>[!signature]
>> `Tensor.add(other, *, alpha=1) -> Tensor`
>> 
>
>>[!Documentation]
>>Add a scalar or tensor to `self` tensor. If both `alpha` and `other` are> specified, each element of `other` is scaled by `alpha` before being used.
>>
>>When `other` is a tensor, the `shape` of other must be broadcastable with the shape of the underlying tensor
>>
>>>[Link](https://pytorch.org/docs/stable/generated/torch.Tensor.add.html#torch.Tensor.add)
```python
tensor = torch.tensor([1, 2, 3])
print(tensor + 10)
print(tensor.add(10))
``` 


### Multiply
>[!info]-
>>[!signature]
>> `Tensor.multiply(value) → Tensor`
>
>>[!Documentation]-
>>Add a scalar or tensor to `self` tensor. If both `alpha` and `other` are specified, each element of `other` is scaled by `alpha` before being used.
>>
>>When `other` is a tensor, the `shape` of `other` must be broadcastable with the shape of the underlying tensor
>>>[Link](https://pytorch.org/docs/stable/generated/torch.Tensor.multiply.html)

```python
tensor = torch.tensor([1, 2, 3])
print(tensor * 10)
print(tensor.multiply(10))
``` 

```python
tensor_1 = torch.tensor([1, 2, 3])
tensor_2 = torch.tensor([4, 5, 6])
print(tensor_1 * tensor_2)
print(tensor_1.multiply(tensor_2))
``` 

>[!note]
> There is a difference between multiplying by a **scalar** and multiplying by a tensor!
### Matrix Multiplication
>[!info]-
>>[!signature]
>> `Tensor.matmul(tensor2) → Tensor`
>
>>[!Documentation]-
>>>[Link](https://pytorch.org/docs/stable/generated/torch.matmul.html#torch.matmul)

```python
tensor_1 = torch.tensor([[1, 2, 3],
                         [4, 5, 6]])
tensor_2 = torch.tensor([[1, 2],
                         [3, 4],
                         [5, 6]])

print(torch.matmul(tensor_1, tensor_2))
print(tensor_1 @ tensor_2)
``` 
>[!note]
>Inner dimensions must match (see [[PyTorch Datatypes#Checking shape of a tensor|shapes]])
> `(2, 3) @ (3, 2)`
> `(3, 2) @ (2, 3)`
