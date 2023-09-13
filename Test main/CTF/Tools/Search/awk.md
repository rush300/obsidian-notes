```bash
cat /home/kali/.local/share/sqlmap/output/api.vulnnet.thm/dump/blog/users.csv | awk -F ',' '{print $2}' > passwords.txt
```
[[john]]
