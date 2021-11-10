# tmux

- copy text:
Enter copy mode: C-b [
Start selecting: C-SPC
Move
Copy: Alt-w
Paste: C-b ]

- send pane to new window:
`C-b !`

- new named session:
`tmux new -s {{session-name}}`

- attach to named session:
`tmux (attach|a) -t {{session-name}}`

- list sessions:
`tmux ls`

- kill session:
`tmux kill-session -t {{session-name}}`
