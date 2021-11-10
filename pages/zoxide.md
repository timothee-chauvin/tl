# zoxide

- default database location:
`~/.local/share/zoxide/`

- interactive selection using fzf:
`zi {{...}}`

- algorithm: https://github.com/ajeetdsouza/zoxide/wiki/Algorithm#matching

- override the algorithm to specify a real path:
`z ~/{{path}}`
`z {{relative_dir}}/`
(from the docs, although it seems that the trailing / is not needed)

- supported:
`z ..`
`z -`

- move a file to a location reached by zoxide:
`mv {{file}} $(z {{loc}} && pwd)`
