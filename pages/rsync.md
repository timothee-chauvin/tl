# rsync

- basically like cp, but better:
`rsync -avh --progress`
(archive, verbose, human-readable)

- archive mode (equivalent of -rlptgoD):
`-a`
(r: recursive
l: symlinks. When symlinks are encountered, re-create the symlink on the destination
p: preserve permissions
t: transfer modification times along with the files and update them on the remote system
g: preserve groups
o: set the owner of the destination file to be the same as the source file, but only if the receiving rsync is being run as the super-user
D: same as --devices --specials.
--devices: transfer character and block device files to the remote system to recreate these devices (only if receiving rsync is super-user)
--specials: also transfer special files like sockets and fifos)

- copy directories recursively:
`-r`
