```bash
curl 144.126.224.27 -H 'Host: localhost'
```
### Use Burp Intruder

- Payload positions
- unchecked 'Update Host header to match target'
- Payload sets: Simple list
- Add FUZZ parameter on subdomain
- Import list of domain-names or dns records

### FFUF
```bash
ffuf -H 'Host: FUZZ' -w hosts.txt -u http://144.126.122.25
```
hosts.txt -> 
localhost
zeus.j3p1vest.ctfio.com
store.j3p1vest.ctfio.com
app-admin.j3p1vest.ctfio.com
app-api.j3p1vest.ctfio.com
app-dev.j3p1vest.ctfio.com
admin.j3p1vest.ctfio.com

## Check the content of the vhost

1. Try to open in browser
2. Try with curl
3. Add the host to your local hosts file
- `nano /etc/hosts`
- Add 144.126.223.26 zeus.j3p1vest.ctfio.com
4. Revisit http://zeus.j3p1vest.ctfio.com

### FUZZ for subdomains 
```bash
ffuf -H 'Host: FUZZ.zeus.j3p1vest.ctfio.com' -w hosts.txt -u http://144.126.122.25
```
### FUZZ for endpoint
```bash
ffuf -H 'Host: store.zeus.j3p1vest.ctfio.com' -w hosts.txt -u http://144.126.122.25/FUZZ
```