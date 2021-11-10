# qpdf

- extract a range of pages:
`qpdf {{input.pdf}} --pages . {{1-10}} -- {{output.pdf}}`

- merge 2 PDF files:
`qpdf --empty --pages {{file1.pdf}} {{file2.pdf}} -- {{merged.pdf}}`
