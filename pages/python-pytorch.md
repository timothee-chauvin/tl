# pytorch

- go from shape [a, b] to [a, b, 1]:
`t.unsqueeze(dim=-1)`

- initialize a random tensor from a shape:
`t = torch.randn({{(1, 2, 3)}})`

- same but with integers, not floats:
`t = torch.randint(low={{0}}, high={{100}}, size={{(1, 2, 3)}})`

- get the size of the ith dimension:
`t.size({{i}})`

- turn off automatic differentiation, if no training is done (only inference):
`torch.set_grad_enabled(False)`

- compare two tensors:
`torch.allclose({{t1}}, {{t2}})`
