CTF scans
```bash
nmap -A 10.10.192.58 -oN scan.initial
namp --top-ports 30 -A 10.10.26.125
namp -A -p- 10.10.26.125 -v
```
Bug Bounty scans
```bash
nmap -A -F 10.10.11.161 -v
namp T2 -A -F 10.10.11.161 -v
```
