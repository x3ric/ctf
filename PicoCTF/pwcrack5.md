
```python
import hashlib

def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])

def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()

with open("./level5.hash.bin", "rb") as f:
    correct_pw_hash = f.read()
with open("./level5.flag.txt.enc", "rb") as f:
    flag_enc = f.read().decode()
with open("./dictionary.txt", "r") as f:
    passwords = f.read().splitlines()
for password in passwords:
    if hash_pw(password) == correct_pw_hash:
        print(f"[+] Password found: {password}")
        decrypted_flag = str_xor(flag_enc, password)
        print(f"[+] Flag: {decrypted_flag}")
        break
```
