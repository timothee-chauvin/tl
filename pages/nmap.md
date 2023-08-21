# nmap

- basic:
`nmap {{host}}`

- only scan a port range:
`-p {{22}}, -p {{1-65535}}, -p {{U:53,111,T:21-25,80}}`

- scan all ports:
`-p-`

- version detection:
`-sV`

- run the default set of scripts:
`-sC`
