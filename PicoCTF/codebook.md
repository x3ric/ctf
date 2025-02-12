
```python
codebook = "azbycxdwevfugthsirjqkplomn"
password = (codebook[4] + codebook[14] + codebook[13] + codebook[14] +
            codebook[23] + codebook[25] + codebook[16] + codebook[0] +
            codebook[25])
print("Indices:", [4, 14, 13, 14, 23, 25, 16, 0, 25])
print("Password characters:", [codebook[i] for i in [4, 14, 13, 14, 23, 25, 16, 0, 25]])
print("Resulting password:", password)
flag_enc = [chr(0x13), chr(0x01), chr(0x17), chr(0x07), chr(0x2c), 
            chr(0x3a), chr(0x2f), chr(0x1a), chr(0x0d), chr(0x53), 
            chr(0x0c), chr(0x47), chr(0x0a), chr(0x5f), chr(0x5e), 
            chr(0x02), chr(0x3e), chr(0x5a), chr(0x56), chr(0x5d), 
            chr(0x45), chr(0x5d), chr(0x58), chr(0x31), chr(0x0d), 
            chr(0x58), chr(0x0f), chr(0x02), chr(0x5a), chr(0x10), 
            chr(0x0e), chr(0x5d), chr(0x13)]

def str_xor(secret, key):
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])

flag_enc_str = ''.join(flag_enc)
flag = str_xor(flag_enc_str, password)
print(flag)
```
