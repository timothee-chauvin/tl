# pacman

- list explicitly installed packages (i.e. not as dependencies):
`pacman -Qqe`

- remove now useless files from /var/cache/pacman:
`pacman -Sc`o

- remove a package and its now unneeded dependencies:
`pacman -Rcns`

- remove all the useless packages on the system (dependencies that weren't removed with the packages):
`pacman -R $(pacman -Qdtq)`

- show which package (already installed) owns a command:
`pacman -Qo {{command}}`

- show which packages (not necessarily installed) own a file:
`pacman -F {{filename}}`
first create/update the database:
`pacman -Fy`

- update a single package:
`pacman -S {{package}}`
(after pacman -Sy)
