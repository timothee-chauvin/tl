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
`rg -P -n "[^[:ascii:]]"`
`rg -P -n "[\x80-\xFF]"`

- treat pattern as a literal string rather than a regex:
`(-F|--fixed-strings)`

- use the PCRE2 engine to use e.g. lookaround assertions:
`--pcre2`

- don't display filenames even if searching multiples files:
`(-I|--no-filename)`

- count number of occurrences, include a 0 when it's 0 rather than printing nothing:
`(-c|--count) --include-zero`

- don't use colors even if printed to the terminal:
`--color never`
