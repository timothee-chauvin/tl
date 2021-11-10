# rg, ripgrep

- also search CVS ignored files:
`--no-ignore`

- also search hidden files:
`--hidden`

- also search binary files:
`--binary`

- only list matching filenames:
`(-l|--files-with-matches)`

- search binary files as if they were text:
`(-a|--text)`

- disable Unicode mode to search for arbitrary bytes in a binary:
`rg -a '(?-u)\x{{30}}'`

- show lines including non-ASCII characters:
`rg -P -n "[\x80-\xFF]"`
