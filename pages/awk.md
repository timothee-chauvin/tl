# awk

- match a negation of a regex:
`! /pattern/ { {{action}} }`

- specify several characters as field separators:
`-F '[{{chars}}]'`

- exit immediately:
`exit {{exit-status}};`

- print the last field:
`print $NF`

- print the second-to-last field:
`print $(NF-1)`

- print all fields except some:
maybe use cut?

- (probably) faster than sort | uniq -c (show all deduplicated lines with their number of occurrences):
`awk '{arr[$0]++} END {for (i in arr) {print arr[i], i}}'`
(consumed 24GB RAM for a 3.5GB file though)

- use printf:
`awk '{printf "{{format-string}}\n", {{args}}}'`

- keep one every n lines:
`awk 'NR % {{n}} == 0'`

- redirection: like the shell, except filename can be any expression. Use quotes for actual filename:
`{print {{...}} > {{expression}}}`
`{printf {{...}} > "{{file}}"}`
