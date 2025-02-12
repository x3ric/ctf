
```python
from pwn import *

def calculate_little_endian(word):
    hex_values = [format(ord(c), '02x') for c in word]
    hex_values.reverse()
    return ''.join(hex_values).upper()

def calculate_big_endian(word):
    return ''.join(format(ord(c), '02x') for c in word).upper()

try:
    conn = remote('titan.picoctf.net', 59839)
    conn.recvuntil(b'Word: ')
    word = conn.recvline().strip().decode()
    print(f"[+] Got word: {word}")
    little_endian = calculate_little_endian(word)
    big_endian = calculate_big_endian(word)
    print(f"[+] Little Endian: {little_endian}")
    print(f"[+] Big Endian: {big_endian}")
    conn.recvuntil(b'Enter the Little Endian representation: ')
    conn.sendline(little_endian.encode())
    conn.recvuntil(b'Enter the Big Endian representation: ')
    conn.sendline(big_endian.encode())
    print(conn.recvall().decode())
except Exception as e:
    print(f"[-] Error: {e}")
```
