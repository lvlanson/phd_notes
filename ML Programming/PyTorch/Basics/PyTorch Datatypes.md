---
aliases:
  - pytorch datatypes
---


>[!attention]
>Run the code below first for importing necessary libraries!
>```python
>import torch
>```
### Tensor
```python
# create a scalar
scalar = torch.tensor(7)
# create a vector
vector = torch.tensor([1,2])
# create a matrix
matrix = torch.tensor([[1,2],
					   [3,4]])
# create a tensor
tensor = torch.tensor([[
						[1,2],[3,4]
					   ],[
						[4,5],[6,7]
					   ]])
print(f"{scalar=}")
print(f"{vector=}")
print(f"{matrix=}")
print(f"{tensor=}")
```

### Checking dimensionality of a tensor
```python
print("Dimensionalities")
print("scalar:", scalar.ndim)
print("vector:", vector.ndim)
print("matrix:", matrix.ndim)
print("tensor:", tensor.ndim)
```
>[!note]
>The levels of square brackets `[...]` used expresses the dimensionality

### Checking shape of a tensor
```python
print("Dimensionalities")
print("scalar:", scalar.shape)
print("vector:", vector.shape)
print("matrix:", matrix.shape)
print("tensor:", tensor.shape)
```
>[!note]
>Each index indicates the amount of elements in each dimension. 
>```python
>t = torch.tensor([[[[1,2,3]]]])
>print(t.shape)
>``` 