# sort

- sort starting from a field number until the end of the line:
`-k {{n}}`

- sort by a single field number:
`-k {{n}},{{n}}`

- sort by a field, then another field:
`-k {{n}},{{n}} -k {{m}},{{m}}`

- specify the field separator:
`-t {{sep}}`

- stable sort:
`-s, --stable``

- sort by a field, then another field, but using different separators:
`sort {{by secondary field}} | sort {{by primary field}} -s`

- randomize lines:
`sort -R`

- more performant than and equivalent to `sort | uniq` for huge files:
`sort -u`
Doesn't work for `uniq -c`, though.
