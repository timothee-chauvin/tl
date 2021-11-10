# UEFI

- show UEFI boot manager entries:
`efibootmgr -v`

- fallback paths:
One of the entries is often something like "USB HDD" without more info. In this case, it inspects every partition on the drive, looking for an ESP. Within the ESP, it looks for \EFI\BOOT\BOOT{some-name}.efi, and executes that. That's how live USBs (e.g. Ubuntu installer) work.
