# tr

Reads from stdin.

- can't replace one character with several. Use something else.

- replace a character with another:
`tr {{find_char}} {{replace_char}}`

- map each character of the first set to the corresponding character of the second set:
`tr '{{abcd}}' '{{efgh}}'`

- delete all occurrences of the specified set of characters:
`tr -d '{{abcd}}'`

- compress a series of identical characters to a single character:
`tr -s '{{abcd}}'`
