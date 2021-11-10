# cut

- use bytes, characters or fields, respectively:
`-b, -c, -f`

- using fields, specify separator:
`-d {{sep}}`

- using fields, keep only field number n (starting from 1):
`-f {{n}}`

- keep only a range of characters from each line (starting from 1):
`-c {{n1-n2}}`

- can specify a list of ranges:
`-c 1,4-6,10-20`

- remove a range of characters from each line:
`-c {{n1-n2}} --complement`

- remove the first n characters from each line:
`-c {{n+1}}-`

- remove the last n characters from each line:
`| rev | cut -c {{n+1}}- | rev`
