# docker run

- a docker container should have Internet connectivity by default. It copies /etc/resolv.conf from the host so check out for network changes since the docker run.

- detach (run the container in the background and only print its new container ID):
`-d`

- interactive (keep stdin open even if not attached):
`-i`

- allocate a pseudo-tty (to then run shells in the container with docker-exec):
`-t`
