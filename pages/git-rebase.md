# git-rebase

- interactive mode:
`git rebase -i`

- change the last 3 commits a little, interactively:
`git rebase -i HEAD~3`

- replay the changes of branch1 onto branch2 (then switches to branch2):
`git rebase {{branch1}} {{branch2}}`
(don't use HEAD, use the real branch names)

- replay the changes of another branch on the current branch:
`git rebase {{other-branch}}`

- abort a rebase that's not going well:
`git rebase --abort`
