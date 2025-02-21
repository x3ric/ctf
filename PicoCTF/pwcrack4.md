
```python
import hashlib

enc_flag_path = "./level4.flag.txt.enc"
hash_bin_path = "./level4.hash.bin"

with open(enc_flag_path, "rb") as f:
    flag_enc = f.read()

with open(hash_bin_path, "rb") as f:
    correct_pw_hash = f.read()

pos_pw_list = [
    "8c86", "7692", "a519", "3e61", "7dd6", "8919", "aaea", "f34b", "d9a2", "39f7", "626b", "dc78", "2a98", "7a85", "cd15", "80fa", "8571", "2f8a", "2ca6", "7e6b", "9c52", "7423", "a42c", "7da0", "95ab", "7de8", "6537", "ba1e", "4fd4", "20a0", "8a28", "2801", "2c9a", "4eb1", "22a5", "c07b", "1f39", "72bd", "97e9", "affc", "4e41", "d039", "5d30", "d13f", "c264", "c8be", "2221", "37ea", "ca5f", "fa6b", "5ada", "607a", "e469", "5681", "e0a4", "60aa", "d8f8", "8f35", "9474", "be73", "ef80", "ea43", "9f9e", "77d7", "d766", "55a0", "dc2d", "a970", "df5d", "e747", "dc69", "cc89", "e59a", "4f68", "14ff", "7928", "36b9", "eac6", "5c87", "da48", "5c1d", "9f63", "8b30", "5534", "2434", "4a82", "d72c", "9b6b", "73c5", "1bcf", "c739", "6c31", "e138", "9e77", "ace1", "2ede", "32e0", "3694", "fc92", "a7e2"
]

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
