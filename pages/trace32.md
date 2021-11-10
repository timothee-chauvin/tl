# trace32

- sofware vs onchip breakpoints
default: software. If fails, falls back to onchip.
software breakpoint: the instruction is patched by a special instruction (usually TRAP) to return control to debugger
onchip: limited number. When CPU supports it. Allows to set breakpoints in ROM.
Breakpoints can be set in the flash memory (which is patched).

- set/delete a breakpoint:
`b.set {{address}} [/(onchip|soft)]`
`b.delete {{address}}`

- set a breakpoint in initialization code:
set the breakpoint while the device is down, then start the device. Works at least with onchip breakpoints.

- can modify registers or memory at any point

- address range syntax:
`{{start}}--{{end}}`

- dump memory to a file
`data.save.binary {{file-path}} 0x{{start}}--0x{{end}}`

- set a breakpoint at an address, for a specific value of a register:
`b.set {{hex_address}} /condition Register({{r11}})==0x{{hex_address}}`
(needs to be at a breakpoint already to set this breakpoint, or from the init file)
(execution much slower)

- can also set a breakpoint to break only every N times, with the UI
didn't look for the corresponding command

- search for a string in memory:
from the Data.dump window, click "Find" then search for the string surrounded by quotes

- nice feature:
type any command prefix and hit Up and Down to navigate history

- logical AND:
&&, but without any spaces, like Register(r0)=0&&Register(r1)=1

- awesome trick to break and immediately return:
`b.set {{address}} /cmd "b.s 00000000" /resume`
(doesn't work without the useless /cmd)
