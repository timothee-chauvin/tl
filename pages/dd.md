# dd

dd is overrated to copy files to/from raw devices: https://www.vidarholen.net/contents/blog/?p=479.
cat, cp, simple redirections work just as well (and can very possibly have a better performance).
(pv is good for monitoring progress)

- write specific bytes at a specific offset:
`printf '{{\x31\xc0\xc3}}' | dd of={{device/file}} bs=1 seek={{100}} count={{3}} conv=notrunc`

- giving an hexadecimal address:
`seek=$(({{0x100}}))`

- read from file instead of stdin:
`if={{file}}`

- write to file instead of stdout:
`of={{file}}`

- specify block size (default 512):
`bs={{bytes}}`

- copy only N blocks:
`count={{N}}`

- show progress:
`status=progress`

- do not truncate the output file:
`conv=notrunc`

