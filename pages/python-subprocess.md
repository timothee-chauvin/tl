# python-subprocess

- get stdout of a command:
`subprocess.run([{{'ls', '-l'}}], stdout=subprocess.PIPE).stdout.decode("utf-8")`

- give command as string:
`subprocess.run("{{echo hello}}", shell=True)`
