
```python
def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])

with open('level1.flag.txt.enc', 'rb') as f:
    flag_enc = f.read().decode()
password = "8713"
decrypted_flag = str_xor(flag_enc, password)
print(decrypted_flag)
```
