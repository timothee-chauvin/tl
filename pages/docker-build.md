# docker-build

Build an image from a Dockerfile.

- A challenge is to access private resources without leaking secrets in the Docker image.
Solution:
`DOCKER_BUILDKIT=1 docker build --secret {{...}} {{...}}`
First line of the Dockerfile:
`# syntax=docker/dockerfile:experimental`
Then:
`RUN --mount=type={{secret}}[,id={{key}}][,required]`
For SSH in particular:
`DOCKER_BUILDKIT=1 docker build --ssh default {{...}}`
(default = the Unix socket at $SSH_AUTH_SOCK)
`DOCKER_BUILDKIT=1 docker build --ssh {{key1=private-key-file1}} --ssh {{key2=private-key-file2}} {{...}}`
Then:
`RUN --mount=type=ssh`
`RUN --mount=type=ssh,id={{key1}}`
The command is then made aware of an SSH agent that can sign requests needed for SSH connections, but never sees the private key.

- remove intermediate containers after successful build (default: true):
`--rm`
