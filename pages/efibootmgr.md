# efibootmgr

EFI boot manager

- show all entries:
`sudo efibootmgr -v`

- rename a boot entry:
`sudo efibootmgr --bootnum {{0001}} --delete-bootnum`
`sudo efibootmgr --create --disk {{/dev/sda}} --part 1 --label 'Ubuntu External SSD' --loader \\EFI\\ubuntu\\shimx64.efi`

- change boot order:
`sudo efibootmgr --bootorder {{0001,001C,etc(hex)}}`

- delete a boot entry:
`--bootnum {{bootnum}} --delete-bootnum`
