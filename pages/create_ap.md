# create_ap

Create a Wifi access point.

- install on arch: linux-wifi-hotspot package

- create an AP:
`sudo create_ap {{wifi_interface (e.g. wlp3s0)}} {{interface_with_internet (e.g. wlp3s0)}} {{AP_name}} {{AP_passwd}} --freq-band 2.4`

- if devices can connect to the AP but don't have internet access, make sure the packets get forwarded, a brutal solution:
`sudo iptables -P FORWARD ACCEPT`
