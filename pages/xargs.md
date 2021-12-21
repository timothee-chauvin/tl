# xargs

- don't run the command if there is no non-blank character (but default, runs once):
`-r`

- read from a file rather than stdin (useful to e.g. use `yes` for stdin):
`-a {{file}}`

- reopen stdin as /dev/tty in the child process before executing the command (useful to run interactive application):
`-o`

- only supply one line at a time to the command (e.g. if the command doesn't support multiple arguments, like xxd):
`--max-lines=1`

- give a pipeline to xargs:
`xargs sh -c "{{pipeline}}"`
