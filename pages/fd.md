# fd

- don't ignore CVS-ignored files:
`-I`

- don't ignore dot files:
`-H`

- specify a max depth (lowest meaningful is 1):
`(--max-depth|-d) {{n}}`

- install on Debian-based distros:
`apt install fd-find`
then binary is named fdfind

- keep only the basename instead of the entire relative path:
`fd {{...}} | awk -F/ '{print $NF}'`

- only files:
`(-t|--type) (f|file)`
