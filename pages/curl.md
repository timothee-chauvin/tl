# curl

- supply a cookie
`-H "Cookie: {{cookie}}"`

- accept self-signed and otherwise invalid certificates:
`curl --insecure https://{{address}}`

- silent (no progress info):
`(-s|--silent)`

- post:
`-X POST`

- supply data:
`-d '{{data}}'`

- specify content type:
`-H "Content-Type: {{application/json}}"`
