# pytorch

- go from shape [a, b] to [a, b, 1]:
`t.unsqueeze(dim=-1)`

- initialize a random tensor from a shape:
`t = torch.randn({{(1, 2, 3)}})`

- get the size of the ith dimension:
`t.size({{i}})`
