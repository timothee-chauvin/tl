# ARM

- assemble small numbers of instructions:
kstool (shipped with keystone)

- general syntax:
`{{mnemonic}}[{{suffix}}][{{condition}}] [{{dest-reg}}], {{operand1 (register or immediate value)}}, {{operand2 (flexible)}}`

- suffixes for half words and bytes
`h, sh = half word, signed half word`
`b, sb = byte, signed byte`

- special purpose registers
r7: syscall number (to do a syscall)
r11: frame pointer
r12: intra procedural call (IP) (scratch register)
r13: stack pointer
r14: link register (LR). Stores the value of the next PC during a function call. Makes it faster than x86 (which always uses a stack position) for leaf functions.
r15: program counter
CPSR: current program status register

- function call:
r0 through r3 for the first arguments, then stack (these are scratch registers)
return value into r0.

- program counter:
When debugging, PC points two instructions ahead of the current PC value

- CPSR (current program status register):
holds flags (overflow, carry, zero, endianness, negative, thumb mode, current privilege mode, etc)

- notable instructions:
blx = branch with Link and eXchange. with Link = first save the next PC into LR. exchange = exchange between ARM and Thumb modes (depending on the value of the last bit of LR). Allows to call functions from a different mode.
ldm = load multiple
stm = store multiple
only ldr (load) and str (store) (and ldm, stm) can access memory (that's what makes it a RISC)

- load value at address pointed to by rb into ra:
`ldr ra, [rb]`

- store ra into address pointed to by rb:
`str ra, [rb]`

- store ra, rb, and r1 to r3, into range at address pointed to by rc (PC and SP cannot be in the list):
`stm rc, {ra, rb, r1-r3}`

- load into ra, rb, and r1 to r3, the range at address pointed to by rc (PC and SP cannot be in the list):
`ldm rc, {ra, rb, r1-r3}`

- exclamation mark ! (writeback)
`stm r1!, {r3, r4, ip, lr}`
means: write r3 to [r1], r4 to [r1+4], etc, and finally set r1 += 16.

- reference to address found in a register (two uses of [] here):
`[{{reg}}[,{{offset}}]]`

- offset can be an immediate, a register, or a scaled register as in ldr r3, [r1, r2, LSL#2]

- the stack pointer can point to the last element of the stack, or the first empty element. Also, the stack can grow up or down. Results in:
(stm|ldm)(db, ib, da, ia) with db = decrement before, ib = increment before, da = decrement after, ia = increment after

- a veneer is a way for a branch instruction to target the full 4GB (in 32 bits) address space. Can't by default since the entire instruction is 4 bytes.

- shifts:
LSL/LSR = Logical Shift Left/Right

- other instructions:
uxth = unsigned to half. Zero-extends the lowest 16 bits.

- load DEADBEEF into a register
`movw r0, #0xBEEF`
`movt r0, #0xDEAD`
