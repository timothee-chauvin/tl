# netcat, nc, ncat

Best versions are OpenBSD's netcat and nmap's ncat. Described below: GNU netcat (TODO).

- listener mode:
`nc -l -p {{port}}`

- connection mode:
`nc {{hostname}} {{port}}`

- UDP (default is TCP):
`(-u|--udp)`
In UDP mode, netcat will accept the first packet from any port, but then will only accept from that port.
