# ghidra

- see the call graph around one function:
`Window -> Function Call Graph`
(can double-click on functions to focus on them)
or:
`Window -> Function Call Tree`

- something like `variable._0_1_`:
happens when the size of the access differs from the size of the variable
(e.g. extracting the first byte of a 4-byte integer).
The first value is the index of extraction, the second the size of extraction.

- highlight all occurrences of variable:
`middle click`
better: enable it on left click in Edit -> Tool Options -> Listing Fields -> Cursor Text Highlight

- structs:
recognize them with variable accessed with different offsets. To start:
`right click, Auto Create Structure`
Then rename and retype fields as usual. Structure editor:
`right click, Edit Data Type`

- go to an address or an exact function / label name:
`g`

- can split a variable as 2 variables:
`right click -> Split out...`

- opposite: merge 2 variables:
ensure they have the same type in both the listing view and the decompiler; rename `var2` to `var1$1` -> now both are var1

- add custom scripts:
Window -> Script Manager -> "Manage Script Directories" -> Add.
Check the "In Tool" column to enable the script.

- show a graph of the basic blocks:
`Window -> Function Graph`

- ARM analysis:
use the ARM aggressive instruction finder

- memory search is much faster than (although not equivalent to) program text search

- get the memory map:
Window -> Memory Map
