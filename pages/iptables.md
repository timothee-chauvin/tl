# iptables

- after running commands, the rules are automatically applied, but not persistent.

- save rules for them to work across reboots (Ubuntu):
`sudo iptables-save | sudo tee /etc/iptables/rules.v4`

- save rules for them to work across reboots (Arch Linux):
`sudo iptables-save -f /etc/iptables/iptables.rules`

- change default policy:
`sudo iptables -P {{(FORWARD|INPUT|OUTPUT)}} {{(ACCEPT|REJECT|DROP)}}`

- allow traffic on some port:
`sudo iptables -A {{INPUT}} -p {{tcp}} --dport {{80}} -j ACCEPT`

- remove a rule:
`sudo iptables -L {{INPUT}} --line-numbers`
`sudo iptables -D {{INPUT}} {{<line_number>}}`
