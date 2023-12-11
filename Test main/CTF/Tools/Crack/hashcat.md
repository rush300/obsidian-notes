```bash
hashcat -m hashes.txt /usr/share/wordlists/rockyou.txt --show

(Mode code 400 for wordpress)
hashcat --example-hashes | grep <your hash>
hashcat -m 400 -a 0 hashes.txt /usr/share/seclists/Passwords/...10-million-passwords... --show
```
