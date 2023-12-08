```bash
sudo openvpn 'vpnfile.ovpn'
sudo pluma /etc/hosts
nmap -p- secret.htb -v
namp -p 22,80,3000 -A secret.htb -v
```
To-do List:
- Dirb for directory enumeration
- Nikto for basic vuln scan
- ffuf for checking for vhosts
- Navigate/browse the website
- Check the source code for comments
- Check robots.txt... sitemap.xml

```bash
dirb http://secret.htb/
nikto -h http://secret.htb/
ffuf -w /usr/share/wordlists/SecLists/Discovery/DNS/sub... -H "Host: FUZZ.secret.htb" -u http://secret/htb -fs 12872
```
