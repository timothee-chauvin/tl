# POSIX shell

- test whether $string contains a substring:
`case "$string" in`
`    *{{substring}}*) {{...}};;`
`    *) {{...}};;`
`esac`

- test whether file exists, regardless of type:
`[ -e {{file}} ]`

- test whether file exists and is not empty:
`[ -s {{file}} ]`

- test whether a string is empty:
`[ -z {{string}} ]`

- give an hexadecimal number to a command that only accepts decimal (e.g. dd):
`$(({{0x100}}))`

- zero-pad a number:
use printf
