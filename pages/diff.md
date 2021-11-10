# diff

- show 2 columns:
`-y`
(warning, cuts lines if too long)

- compare the filenames of 2 directories:
`diff <(cd {{dir1}} && fd -H .) <(cd {{dir2}} && fd -H .)`
