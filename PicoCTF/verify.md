
```bash
ssh -p 58098 ctf-player@rhea.picoctf.net
```

```bash
for file in files/*; do
    if [ -f "$file" ]; then
        ./decrypt.sh "$file"
    fi
done
```
