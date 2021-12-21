# pip

- disable the cache (useful e.g. in Docker images):
`--no-cache-dir`

- install on a machine without Internet access, or on which pip's connectivity is broken:
first on a machine with a working pip:
`mkdir {{package_and_deps}}`
`pip download {{package}} -d {{package_and_deps}}`
copy the directory to the target machine
go into it, then
`pip install {{package.tar.gz|package.whl}} -f ./`
