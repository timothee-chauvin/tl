# ssh

- related commands:
`ssh-keygen [-b 4096] [-C {{comment}}]`
`ssh-copy-id -i {{private-key-file}} {{remote-host}}`

- add a key to the OpenSSH authentication client:
`ssh-add {{private-key-file}}`

- show info about what `user` (you) can do on `host`:
`ssh user@host info`

- run commands:
`ssh user@host "{{commands}}"`

- authentication forwarding (if not already specified in config):
`-A`

- specific port:
`-p {{port}}`
