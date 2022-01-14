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

 -rename window:
`C-b ,`

## .tmux.conf
- location: ~/.tmux.conf

- get tmux to pick up the changes without killing all sessions:
`tmux source ~/.tmux.conf`

- change number of lines saved for future panes (default is only 2000):
`set-option -g history-limit {{50000}}`
(a line isn't delimited by \n, but by the width of the pane, so no risk of massive lines sucking up memory)
