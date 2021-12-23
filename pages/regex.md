# regex: PCRE, ERE, BRE

## PCRE to ERE
\d -> [[:digit:]]
\s -> [[:space:]]

## ERE to BRE
escape: {}, (), ?, +, |

- negative lookahead (match pattern1 not followed by pattern2, not capturing pattern2):
`{{pattern1}}(?!{{pattern2}})`

- positive lookahead:
`{{pattern1}}(?={{pattern2}})`

- negative lookbehind:
`{{pattern1}}(?<!{{pattern2}})`

- positive lookbehind:
`{{pattern1}}(?<={{pattern2}})`
