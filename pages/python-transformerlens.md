# TransformerLens

- get metadata about a model:
`model.cfg`

- compare the expected output to the model's possible outputs:
`utils.test_prompt({{"2 + 2 ="}}, {{" 4"}}, model)`

- see how a sentence gets tokenized into smaller strings:
`model.to_str_tokens({{"Hello, World!"}})`

- get the single token of a string as an integer:
`model.to_single_token({{"John"}})`

- convert string or list of strings into tensor of tokens:
`model.to_tokens({{"string"}}|{{["string1", "string2"]}})`

- run with cache:
`model.run_with_cache({{tokens}})`

- get the final residual stream from the cache without LayerNorm:
`final_residual_stream = cache["resid_post", -1]`

- apply LayerNorm on a residual stream at some layer:
`{{final_residual_stream}} = cache.apply_ln_to_stack({{final_residual_stream}}, layer={{-1}})`

- get the final residual stream from the cache with LayerNorm applied:
`final_residual_stream = cache["ln_final.hook_normalised"]`

- get all partial residual streams:
`cache.accumulated_resid()`

- get the individual contributions of each layer to the residual stream (i.e. differences between adjacent residual streams):
`cache.decompose_resid()`
