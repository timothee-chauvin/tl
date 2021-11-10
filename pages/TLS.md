# TLS

- commands to analyze a TLS-protected Firefox session:
`sudo tcpdump -w /tmp/capture.pcap -i {{interface}}`
`SSLKEYLOGFILE=/tmp/secrets.txt firefox -P --no-remote (using a different profile than the usual one)`
`editcap --inject-secrets tls,/tmp/secrets.txt /tmp/capture.pcap /tmp/capture-secrets.pcapng`
`wireshark /tmp/capture-secrets.pcapng`

- or force the use of HTTP with burp
