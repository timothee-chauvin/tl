# pytest

- only call tests matching a pattern:
`pytest -k "{{test_pattern1 or test_pattern2}}"`

- show the output in real time, and allow to use stdin (e.g. to debug):
`-s`

- don't show the massive error tracebacks with full source code:
`--tb=no`
(--tb options: auto, long, short, line, native, no)

- exit after the first failure:
`-x`
