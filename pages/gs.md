# ghostscript - work with PDFs

- compress a PDF:
`gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile={{output.pdf}} {{input.pdf}}`
