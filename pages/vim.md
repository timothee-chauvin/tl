# vim

- open a file in binary mode (won't append a newline at the end, won't try to interpret as UTF-8):
`vim -b {{file}}`
`:set binary`
edit directly or use `:%!xxd`, then `:%!xxd -r` before saving (can only edit the left part of the xxd output)
