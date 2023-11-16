## Port 
- naabu -> https://github.com/projectdiscovery/naabu

## DNS
- dnsx -> https://github.com/projectdiscovery/dnsx
Search for A records (IP)
Search for CNAME records (domains)
Goal: domain takeover, *zone takeover*
Example: 
```bash
subdomain.doamin.com | dnsx -resp -silent #-rcode noerror,servfail,refused
```
## Web server fingerprinting 
- httpx -> https://github.com/projectdiscovery/httpx