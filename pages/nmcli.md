# nmcli

- list the available wifi networks:
`nmcli device wifi list`

- set a connection up or down:
`nmcli conn [up|down] {{connection-name}}`

- connect to new network:
`nmcli device wifi connect {{connection-name}} password {{password}}`
