# Makefile

- each line is executed in a subshell, so to e.g. cd somewhere, do that on the same line separated by ';'
`cd {{somewhere}}; command`
`cd {{somewhere}}; \`
`  command`

- supply a variable:
`make {{target}} {{VAR}}={{sthg}}`

- refer to an externally defined variable from the Makefile:
`$({{VAR}})`

- test if a variable is defined for all targets:
`ifndef {{variable}}`
`$(error "{{message}}")`
`endif`

- test if a variable is defined only for a certain target:
`test -n "$({{variable}})" || (echo "{{message}}"; exit 1)`

- don't output an expanded command before running it:
`.SILENT: {{target}}`
`@{{command}}`
`make -s`
