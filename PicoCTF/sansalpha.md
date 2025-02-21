
```bash
sshpass -p 'f3b61b38' ssh -o StrictHostKeyChecking=no -p 60471 ctf-player@mimas.picoctf.net
```

ls and last commnad

```bash
*; $_
```

results in `on-calastran.txt`

in the next path

```bash
*/*; 
```

results in `blargh/flag.txt` and `blargh/on-alpha-9.txt`

now we can use the letters in the variable `$_`

to create our commands

```bash
${_:3:2} -> ca
${_:8:1} -> t
```

```bash
*; ${_:3:2}${_:8:1} */*
```
