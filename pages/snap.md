# snap

- install an app without strict confinement (to allow it to access files, etc):
`sudo snap install {{app}} --classic`

- remove a package without saving a snapshot of its data:
`sudo snap remove {{app}} --purge`

- update a package:
`sudo snap refresh {{app}}`

- show info about a package, including which channels can be tracked:
`snap info {{app}}`

- install from a specific channel (e.g. install an older version):
`sudo snap refresh {{app}} --channel={{channel}}`
