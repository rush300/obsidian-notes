*Scan*
```bash
smbclient -L //10.10.26.125
```

*Connect to server:*
```bash
smbclient //10.10.26.125/websvr
ls
```

*Get resource*
```bash
get enter.txt
exit
```
```bash
cat enter.txt
```
