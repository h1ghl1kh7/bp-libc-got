# bp_libc_got

Set Breakpoint at the address in the .got.plt section of the libraries loaded in the target process.

# Features

libc arg is optional, if not specified, the script will attempt to find the libc paths in the target process. (default : None)

flag arg is optional too, if True : make breakpoints work after any preceding breakpoint is hit. / False : make breakpoints work immediately. (default : False)

it returns 1 if successful, 0 if not.

# Usage

## In a pwntools script

```python
from pwn import *
import bp_libc_got

p = process("chal")
_, gdb_api = gdb.attach(p, gdbscript="b *vuln", api=True)

bp_libc_got.bp_got(gdb_api = gdb_api, libc = "libc.so.6", flag = True)
```
