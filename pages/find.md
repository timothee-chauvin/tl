# find

- (f)ile, (d)irectory:
`-type (f|d)`

- executable:
`-executable`

- exclude files in a directory:
`-not -path "{{path}}"`
`-not -wholename "*/{{directory}}/*"`

- find the hard links for some file:
`find {{.}} -samefile {{filename}}`

- specify max depth (lowest meaningful is 1):
`-maxdepth {{n}}`
