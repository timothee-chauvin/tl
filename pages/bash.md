# bash

- redirect here document: multiple options (https://unix.stackexchange.com/a/88492/453559), including:
`{`
`cat << EOF`
`...`
`EOF`
`} | {{command}}`

- force interpreting a number as decimal, even if it starts with 0:
`$((10#{{number}}))`

- extract substrings:
`${var:{{start-offset}}:{{size}}}`

- stdin into a variable:
`myvar=$(</dev/stdin)`
