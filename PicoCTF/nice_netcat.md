
```bash
python3 -c "from pwn import *; c=remote('mercury.picoctf.net',22342); print(''.join(chr(int(x)) for x in c.recvall().split()))"
```
