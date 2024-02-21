# Find top 5 domains
```dork
site:redhat.com inurl:login
```
Owned by IBM:
IBM.com
RedHat.com
pwc.com

```bash
cat domains.txt | grep Wildcard | awk '{print $1}' | sed 's/*//g'

echo "https:wwww.regions.com" | getallurls | grep "api/" | httpx -title
```

