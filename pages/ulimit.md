# ulimit

- ulimit is a shell built-in! It will only apply in the current shell, at least for the regular changes like ulimit -c 0. Maybe not for the hard limits.

- disable core dumps:
`ulimit -c 0`
