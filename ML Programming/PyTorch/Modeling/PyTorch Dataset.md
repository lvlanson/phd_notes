---
aliases: 
- PyTorch Dataset
---

>[!Setup]
>``` python
>from torch.utils.data import Dataset
>
>class MyCustomDataset(Dataset):
>
>	def __init__(self, *args, **kwargs):
>		pass
>		# setup attributes here
>
>	def __len__(self):
>		pass
>		# setup method which returns the length of the dataset
>		
>	def __getitem__(self, idx):
>		pass
>		# setup method such that myDataSet[i] returns a data point at index i
>``` 
