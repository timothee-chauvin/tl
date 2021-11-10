# watch

Caution with `watch pgrep -f {{something}}`: watch adds a few processes containing {{something}} in their command line, giving an unexpected list of processes.

- watch a command every x seconds:
`watch -n {{x}} {{command}}`

- watch a pipeline:
`watch "{{pipeline}}"`
