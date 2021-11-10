# date

- Unix timestamp (integer) into human-readable string:
`date -d @{{timestamp}}`
`date --date='@{{timestamp}}'`

- show the number of seconds since the Epoch (Unix timestamp):
`date +%s`

- specify a date:
`-d '{{date}}'`
`--date='{{date}}'`

- use a specific format string:
`date +{{format-string}}`

- YYYY-MM-DD:
`date +%Y-%m-%d`

- hour, minute, second:
`%H %M %S`

- day of the week (e.g. Monday):
`%A`
