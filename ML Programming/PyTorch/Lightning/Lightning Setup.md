---
aliases:
- Lightning Setup
---
>[! Basic Setup]
>```python
>import lightning as L
># import possibly other stuff
>
>if __name__ == "__main__":
>	train_loader = DataLoader(CustomDataSet(*args), *args) # Training Data
>	test_loader = DataLoader(CustomDataSet(*args), *args) # Testing Data
>	val_loader = DataLoader(CustomDataSet(*args), *args) # Validation Data
>
>	model = MyLightningModule(*args, **kwargs)
>	
>	trainer = L.Trainer(*args, **kwargs)
>	trainer.fit(model, train_loader)
>	
>```

>[!note]
>The `LightningModule` is defined as described in [[Lightning Module]]