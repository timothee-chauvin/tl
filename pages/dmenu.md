# dmenu

- inspect how it sees the world (e.g. $PATH):
`echo $PATH > /tmp/path`

- change its $PATH:
do it in .xinitrc as it doesn't read .profile or other files, before `exec i3` 
Then rm ~/.cache/dmenu_run and log out.
