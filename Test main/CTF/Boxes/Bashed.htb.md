```
nmap -sC -sV -oA nmap/initial 10.10.10.68
cat nmap/initial.nmap

gobuster -u http://10.10.10.68 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt


```