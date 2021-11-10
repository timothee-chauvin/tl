# sed

- in place:
`-i, --in-place`

- in place with a backup, specifying suffix:
`-i{{SUFFIX}}, --in-place={{SUFFIX}}`

- default: BRE. Doesn't support PCRE. Use ERE instead:
`-E`

- don't print (e.g. there's already a print clause in the command):
`-n`
