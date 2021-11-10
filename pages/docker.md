# docker

- post installation steps:
`sudo groupadd docker && sudo usermod -aG docker $USER`
logout, log back in
`sudo systemctl enable docker.service`

- show all images:
`docker images`

- show all running containers:
`docker ps`

- show all containers, including non-running:
`docker ps -a`

- remove a container:
`docker rm {{name-or-ID}}`

- remove an image:
`docker image rm {{name-or-ID}}`

- troubleshoot a container:
`docker inspect {{name-or-ID}}`

- start a stopped container:
`docker start {{name-or-ID}}`

- show the logs of a container:
`docker logs [(-f|--follow)] {{container}}`

- copy files from/into docker containers:
`docker cp {{container}}:{{path}} {{host-path}}`
`docker cp {{host-path}} {{container}}:{{path}}`

- export and import an image:
`docker save {{image}} > {{archive.tar}}`
`docker load < {{archive.tar}}`

- export and import a container (only filesystem, not mounted volumes):
`docker export, docker import`
