# git-log

- git reflog, but with more info:
`git log -g`

- limit to the most recent commits:
`git log -{{n}}`

- also show the diffs:
`git log --patch`

- also show number of lines added and removed for each file:
`git log --stat`

- one line per commit:
`git log --oneline`

- filter by paths:
`git log [options] -- {{paths}}`

- show where branches and tags point:
`git log --oneline --decorate`

- find commits that changed the number of occurrences of a string in the code:
`git log -S {{string}}`

- see all changes made to some function:
`git log -L :{{function-name}}:{{file}}`

- show dates in the format YYYY-MM-DD:
`git log --format=%as`

- show a lot of info (including committer and author):
`git log --format=fuller`

- show colors even if not outputting to a TTY:
`--color=always`

- show all branches:
`--all`

- show all developers and their email addresses:
`git log --all --format='%an %ae' | sort -u`
