# Assets discovery

1. https://bgp.he.net -> copy AS13335 number
2. Paste it to amass 
```bash
amass intel -asn AS13335
```
3. Do a reverse whois with amass
```bash
amass intel -d domain.com -whois
```
4. Google dork -> "1999-2022 GameStop" inurl:gamestop
5. https://crunchbase.com -> get info for a domain.com

# Subdomain enumeration

Add free API keys for amass and subfinder!
```bash
amass enum -d domain.com -passive -o amass_subdomains.txt

subfinder -d domain.com -silent -t 100 -nc -all > subfinder_subdomains.txt

crobat -s domain.com > crobat_subdomains.txt

puredns bruteforce ~/tools/g0ldenGun/subdomain_wordlist.txt domain.com -w puredns_bf_domains.txt -r ~/tools/g0ldenGun/resolvers.txt

cat amass_subdomains.txt subfinder_subdomains.txt crobat_subdomains.txt puredns_bf_domains.txt | sort -u | anew collected_subdomains.txt

gotator -sub collected_subdomains.txt -perm ~/tools/g0ldenGun/alt_words.txt -depth 1 -numbers 10 -mindup -adv -md -silent > subs_to_resolve.txt

puredns resolve subs_to_resolve.txt -r resolvers.txt --write valid_alt_domains.txt

wc -l subfinder_subdomains.txt (returns line count)
```