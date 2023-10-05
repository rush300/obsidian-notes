```bash
cd lab/crapi
sudo docker-compose start

nmap -sC -sV 127.0.0.1
nmap -p- 127.0.0.1
nmap -sC 127..0.0.1 -p 8025

amass
amass enum -list
amass enum -active -d crapy.apisec.ai
amass enum -active -d microsoft.com | grep api

gobuster dir -u http://127.0.0.1:8888 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -b 200

```