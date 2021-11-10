# gpg

- decrypt file:
`gpg --output {{filename}} --decrypt {{filename.gpg}}`

- create a key pair:
`gpg --full-generate-key`

- list the keys on the system:
`gpg --list-keys`

- determine which filename in ~/.gnupg/private-keys-v1.d corresponds to which key:
`gpg --list-keys --with-keygrip`

- when exporting, use ASCII instead of a binary format:
`--armor`

- output a public key for sharing:
`gpg --export --armor {{email address or key identifier}} [--output {{filename}}]`

- show details about a key file:
`gpg --show-key {{file}}`

- encrypt file symmetrically, with a password:
`gpg (-c|--symmetric) {{file}}`

- decrypt the above: use normal decryption command
