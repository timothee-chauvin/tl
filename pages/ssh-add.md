# ssh-add

Add private keys to an SSH agent.

- for ssh-add to work, first do, if necessary (e.g. Arch):
`eval "$(ssh-agent)"`

- add a specific key:
`ssh-add {{private-key-filename}}`

- list fingerprints of keys represented by the agent:
`ssh-add -l`
