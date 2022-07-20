# git-branch

- create a branch from the current one:
`git branch {{new-branch-name}}`

- rename a branch:
`git branch -m {{old-name}} {{new-name}}`

- print current branch name:
`git branch --show-current`

- show the remote branches associated with each local branch:
`git branch -vv`

- set the remote branch of a branch without pushing (if the remote branch already exists):
`git branch --set-upstream-to={{remote-name}}/{{branch-name}}`

- unset the upstream for a branch:
`git branch --unset-upstream`
