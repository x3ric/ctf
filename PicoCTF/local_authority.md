
<http://saturn.picoctf.net:63579/login.php>

```bash
echo "2196812e91c29df34f5e217cfd639881" > hash.txt
hashcat -m 0 -a 3 hash.txt 'strongPassword?d?d?d?d?d?d'
```

admin

strongPassword098765
