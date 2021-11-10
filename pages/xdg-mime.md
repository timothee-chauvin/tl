# xdg-mime

- change a default application:
`xdg-mime default {{feh.desktop}} {{image/png}}`
(goes into ~/.config/mimeapps.list)

- see the default application for a MIME type:
`xdg-mime query default {{text/plain}}`

- see the MIME type of a file:
`xdg-mime query filetype {{file}}`
