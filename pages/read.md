# read

- general syntax:
`read {{intovar1}} {{intovar2}} etc`

- don't consider backslashes to mean anything (raw):
`-r`

- change the field separator:
`IFS={{@}} read {{...}}`

- disable echoing:
`-s`

- give a prompt:
`-p {{prompt}}`
