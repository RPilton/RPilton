## General guidelines for exploitation from Lecture 2

List the files for the challenge

`ls /challenge`

run the program to try to understand its behaviour

use

`strings /challenge/<binary>`

See if there are any interesting keywords

## Static Analysis tool phase

### Ghidra

New project, import binary, conduct analysis
Look into the functions and check the decomplier for format string, read, write and buffers, follow the prgram flow
Ghidra numbers local variable with the value for how far away from the top of the stack they are in HEX 
e.g. local_48 is 48 hex bytes / 72 Dec bytes away from the top of the stack
e.g. local_8 is 8 hex 8 / 8 Dec bytes away from the top of the stack

Rename known functions

## Command line exploit

Create pwntools exploit template

`pwn template <target binary> > <exploit filename>.py`

Check Binary Security

`pwn checksec <taget buinary>`

Open in GDB

`gdb <target binary`

create a giant input to overflow the buffer

`cyclic 256`

set a break point on ret for the vulnerable function

`info functions`
`disassem main`
`dissassem vuln`
`b *vuln+<code line>`

Run the target binary and check the ret address with 

`cyclic -l <value>`

Note the offset value 




