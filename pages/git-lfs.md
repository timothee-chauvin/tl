# Git LFS

- uses HTTPS, not SSH

- setup:
`git lfs install`
if on a git reference that should resolve Git LFS files:
`git lfs pull`
otherwise will do automatically when switching references

- tell Git to show the diffs of the actual LFS files, not the pointers (making merges impossible):
`git config diff.lfs.textconv cat`

- track files with LFS:
`git lfs track "{{pattern}}"`
notable pattern, track a directory recursively:
`git lfs track "{{directory}}/**"`
