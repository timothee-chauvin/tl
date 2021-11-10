# Python

- equivalent of static variables in C:
`def foo():`
`    try:`
`        foo.counter += 1`
`    except AttributeError:`
`        foo.counter = 0`

- profile a module or script:
`python -m cProfile (-m {{module}}|{{script.py}})`

- int to bytes:
`({{1024}}).to_bytes({{2}}, byteorder='{{big}}')`

- string which can be 0x... to int, appropriate base:
`int("{{str}}", base=0)`
