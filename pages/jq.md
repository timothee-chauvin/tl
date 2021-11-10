# jq

- pretty-print a JSON file:
`jq . {{file}}`

- given an array like [{"code": "P142", "value": "N'Djamena" }, ...], get the value corresponding to the code
`jq ".[] | select(.{{code}} == "{{P142}}").{{value}}" {{file}}`

