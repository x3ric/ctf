
```bash
ssh -p 58098 ctf-player@rhea.picoctf.net
sshpass -p 'f3b61b38' ssh -o StrictHostKeyChecking=no -p 58098 ctf-player@rhea.picoctf.net
```

```bash
for file in files/*; do
    if [ -f "$file" ]; then
        ./decrypt.sh "$file"
    fi
done
```
