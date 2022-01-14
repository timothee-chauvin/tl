# GNU parallel

- read each line from a file and give that as arguments to a command:
`parallel {{command}} < {{file}}`

- give the argument at a specific position:
`parallel {{command}} {} {{other_args}}`
(this is the default, can be changed with -I)

- dry run:
`--dry-run`

- process the input as words, rather than lines:
`--delimiter ' '`
(note the file shouldn't have a final newline in this case, since newlines aren't interpreted anymore)

- silence the citation notice:
`--will-cite`
