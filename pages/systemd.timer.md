# systemd timers

Like systemd unit files, but with a [Timer] section.

- better than below when adequate, i.e. most of the time: systemctl --user.

- list all timers:
`systemctl list-timers [--all]`

- paths:
`etc/systemd/system/{{name}}.timer`
`etc/systemd/system/{{name}}.service`

- after creating the files:
`sudo systemctl start {{name}}.timer`
`sudo systemctl enable {{name}}.timer`
(note: .timer, not .service)

- verify everything's okay:
`systemctl status {{name}}.service`
`systemctl status {{name}}.timer`

- example .service file:
`[Unit]`
`Description={{...}}`
`[Service]`
`ExecStart={{command}}`
(no [Install])

- example .timer file:
`[Unit]`
`Description={{...}}`
`[Timer]`
`OnBootSec=5`
`OnUnitActiveSec=1d`
`[Install]`
`WantedBy=timers.target`

- long ExecStart commands (pipelines etc) seem to cause issues, better run a simple command

- make a realtime timer trigger the service immediately if it missed the last time:
`[Timer]`
`OnCalendar={{...}}`
`Persistent=true`

- durations syntax:
`(OnBootSec|OnUnitActiveSec)=(1|1min|1h|1d|1w)`

- realtime timer syntax:
`OnCalendar=[{{DayOfWeek}}] {{Year}}-{{Month}}-{{Day}} {{Hour}}:{{Minute}}:{{Second}}`

- OnCalendar can be specified more than once.

- run every second:
`OnCalendar=*-*-* *:*:*`

- run the first four days of each month, only if that day is a monday or tuesday:
`OnCalendar=Mon,Tue *-*-1..4 18:00:00`

- run the first saturday of each month:
`OnCalendar=Sat *-*-1..7 18:00:00`

- automatically restart (on failures etc):
`Restart=always`
`RestartSec=1`
