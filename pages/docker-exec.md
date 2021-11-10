# docker exec

- usual syntax:
`docker exec --interactive|-i --tty|-t {{container}} {{bash}}`

- exec more than just e.g. "bash":
`docker exec {{...}} sh -c "{{commands}}"`
