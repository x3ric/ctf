
```bash
python3 -c "exec(\"import socket; s=socket.socket(); s.connect(('saturn.picoctf.net',58126)); print(eval(s.recv(1024).decode()))\")"
```
