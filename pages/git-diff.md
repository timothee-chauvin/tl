# git diff

- only show lines changed, i.e. no context:
`(--unified=0|-U0)`

- go further:
`git diff -U0 | rg '^[+-]' | rg -v '^(--- a/|\+\+\+ b/)'`
