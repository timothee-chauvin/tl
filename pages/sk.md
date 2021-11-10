# sk

- visualize the files in the current directory with some command:
`sk --preview "{{xxd}} {}"`

- pass it a subset of the files in the current directory:
`fd --glob "{{pattern}}" . | sk --preview "{{cat}} {}"`
