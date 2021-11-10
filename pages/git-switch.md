# git-switch

Successor of git checkout, along with git restore.

- switch to a branch and create it at the same time:
`git switch -c {{branch-name}}`

- switch to a remote branch, or anything that's not editable (i.e. in detached HEAD mode):
`(-d|--detach)`

- switch to a local branch created from a remote branch:
`git switch -c {{local-branch-name}} {{remote}}/{{remote-branch-name}}`
