# cryptsetup

- open and mount a LUKS-encrypted device:
`sudo cryptsetup open [--type luks[2]] (/dev/sd{{Xn}}|/dev/disk/by-uuid/{{UUID}}) {{name}}`
`sudo mount /dev/mapper/{{name}} {{mountpoint}}`

- unmount and close a LUKS-encrypted device:
`sudo umount {{mountpoint}}`
`sudo cryptsetup close {{name}}`

- create a LUKS-encrypted device:
make sure the device is unmounted
`sudo cryptsetup luksFormat /dev/sd{{Xn}}`
`sudo cryptsetup open --type luks /dev/sd{{Xn}} {{name}}`
`sudo mkfs.ext4 /dev/mapper/{{name}} [-L {{partition-label}}`
`sudo mount /dev/mapper/{{name}} {{mountpoint}}`

- ask for passphrase twice and verify they match:
`-y`
