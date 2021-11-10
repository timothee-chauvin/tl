# pv

Monitor progress of a pipe

- except that it prints progress on stderr, pv behaves exactly like cat (can take 1 or several files as arguments, will read from stdin if not given any)

- if its input comes from stdin, it can't know the expected size. Specify it:
`pv -s {{size}}`

- example: writing an image to a disk:
`pv {{image-file}} > /dev/{{disk}}`
(it knows about the device size automatically for the ETA)
