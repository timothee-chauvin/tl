# python-cProfile

cProfile and profile are basically the same but profile is written in Python. So cProfile is faster and recommended.
Both are installed by default.

- usage from the command line:
`python -m cProfile -- {{module_to_profile and its arguments}}`
(also usable from within python code)
(can interrupt with C-c, the profiling output will be written before the program terminates)

- profile output in a raw file, to be later parsed using pstats:
`(-o {{outfile}}|--output={{outfile}})`

- sort:
`(-s {{key}}|--sort={{key}})`

- sort keys:
https://docs.python.org/3/library/profile.html#pstats.Stats.sort_stats

- notable sort keys:
time / tottime: time spent in the function (not its descendants)
cumtime / cumulative: time spent in the function and its descendants

- parse output of a raw profiling file:
`import pstats`
`p = pstats.Stats("{{filename}}")`
`p.sort_stats("time").print_stats()`

- profile from the code, enabling and disabling:
`import cProfile`
`pr = cProfile.Profile()`
`pr.enable()`
`{{...}}`
`pr.disable()`
`# Dump raw stats:`
`pr.dump_stats("{{outfile}}")`
