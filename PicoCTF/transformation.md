
```python
def decode_flag(encoded):
    flag = ''
    for c in encoded:
        high_byte = ord(c) >> 8
        low_byte = ord(c) & 0xFF
        flag += chr(high_byte) + chr(low_byte)
    return flag

encoded = "灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸彥㜰㍢㐸㙽"
print(decode_flag(encoded))
```
