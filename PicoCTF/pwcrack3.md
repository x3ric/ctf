
```python
import hashlib

enc_flag_path = "./level3.flag.txt.enc"
hash_bin_path = "./level3.hash.bin"

with open(enc_flag_path, "rb") as f:
    flag_enc = f.read()

with open(hash_bin_path, "rb") as f:
    correct_pw_hash = f.read()

pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]

def hash_pw(pw_str):
    m = hashlib.md5()
    m.update(pw_str.encode())
    return m.digest()

correct_pw = None
for pw in pos_pw_list:
    if hash_pw(pw) == correct_pw_hash:
        correct_pw = pw
        break

def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(secret_c ^ ord(new_key_c)) for (secret_c, new_key_c) in zip(secret, new_key)])

decrypted_flag = str_xor(flag_enc, correct_pw)
print(decrypted_flag)
```
