```bash
ffuf -w wordlist/customlist/all.txt -u http://ps6unii.ctfio.com/FUZZ -ac -ms 200,300,400,405,403,401
```
[[Response codes]]

> [!Important]- SecLists
> https://github.com/danielmiessler/SecLists
> 

---
# TCM
Fuzz for path
```bash
ffuf -u http://team.thm/FUZZ -w /usr/share/wordlists/dirb/common.txt
```
Extended fuzzing
```bash
ffuf -u http://team.thm/FUZZ -w /usr/share/wordlists/dirb/common.txt -e .js,.txt,.sh,.zip
```
Fuzz for subdomains
```bash
ffuf -u http://10.10.192.58 -H "HOST: FUZZ.team.thm" -w /usr/share/wordlists/dirb/common.txt -fs 11366
```
> -fs [exclude results / Size:11366] / excludes results with same size where not found.



> [!IMPORTANT] Bruteforce
> ```bash
ffuf -X POST -u http://ctvqeeay.vulnbegin.co.uk/cpadmin/login -d "username=admin&password=FUZZ" -w /usr/share/wordlists/seclists/Passwords/Common-Credentials/10k-most-common.txt:FUZZ -H "Cookie: $cookie" -H "Content-type: application/x-www-form-urlencoded" -t 2 -p 0.1 -fc 200


> [!IMPORTANT] FUZZ with admin token (cookie)
> 
> ```bash
ffuf -u http://ctvqeeay.vulnbegin.co.uk/cpadmin/FUZZ -w /usr/share/wordlists/dirb/common.txt -H "Cookie: $cookie; token=2eff535bd75e77b62c70ba1e4dcb2873"



> [!IMPORTANT] FUZZ With X-Token (header parameter)
> |api_key|"X-Token: 492E64385D3779BC5F040E2B19D67742"|
> ```bash
ffuf -u http://server.6h0qk1c9.vulnbegin.co.uk/FUZZ -w /usr/share/wordlists/dirb/common.txt -H "Cookie: $cookie" -H "X-Token: 492E64385D3779BC5F040E2B19D67742" -t 2 -p 0.1


> [!IMPORTANT] Look for Virtual Hosts
> Nahamsec
> ```bash
> ffuf -H 'Host: FUZZ' -w hosts.txt -u http://144.126.224.27
> ffuf -H 'Host: store.zeus.j3p1vest.ctfio.com' -w all.txt -u http://144.126.224.27/FUZZ




