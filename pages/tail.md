# tail

- keep all lines except the first n ones:
`tail -n +{{n+1}} {{file}}`

- bytes instead of lines:
`-c {{n}}`

- 2 kinds of follow: by name, or by file descriptor (so continues to follow if file is renamed).

- follow by file descriptor:
`(--follow|-f)`

- follow by name:
`(--follow=name --retry|-F)`

- prefix the lines with the current timestamp, for a tail -F:
`stdbuf -o 0 tail -F {{*}} | while read line; do printf "%s " $(date +{{%H:%M:%S.%N}}); echo "$line"; done`
