# xxd

- plain mode:
`-p`

- reverse mode (xxd output to binary):
`-r`

- make the plain mode output a single line, without newlines:
`xxd -p {{file}} | tr -d '\n'`

- add an offset to the displayed position:
`-o {{offset}}`
(can be specified in hexadecimal)
