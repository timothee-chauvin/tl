# git

- unstage all the currently staged files:
`git reset HEAD .`

- irreversibly revert changes in working directory to what the files looked like after the last commit:
`git checkout -- ({{files}}|.)`

- merge a branch into the master branch:
`git checkout master; git merge {{branch}}`

- adding a file to .gitignore, but this file is already tracked. Do:
`git update-index --skip-worktree {{file}}`

- git update-index --skip-worktree for an entire directory:
`cd {{dir}}; git update-index --skip-worktree $(git ls-files)`

- remove a file only from the staging area:
`git rm --cached {{file}}`

- only add currently tracked files:
`git add -u`

- all commits reachable from ref1 but not from ref2:
`ref2..ref1`

- all commits reachable from either ref1 or ref2, but not both:
`ref1...ref2`

- apply a command (like rm -f myfile) to all commits:
`git filter-branch --tree-filter '{{command}}' {{branch}}`

- copy only the committed files of a git repository elsewhere on the same machine:
`git clone {{path-to-repo}} {{target-path}}`

- show all the files currently tracked by git:
`git ls-files`

- ignore changes to an existing file locally (make Git assume that the working tree version is the same as in the index):
`git update-index --assume-unchanged {{file}}`
