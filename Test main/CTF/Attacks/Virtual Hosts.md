If you have multiple hosts on one IP address, this mean there are virtual hosts exists.

Example: test.com return one page, but the IP address of this host returns different page.

Also can try to use curl for requesting the localhost of the IP address.
```bash
curl 144.126.224.27 -H 'Host: localhost'
```
[[ffuf]]


> [!WARNING] Failed to open a host!
> Try with curl, or add the host to /etc/hosts




Reference: https://www.youtube.com/watch?v=lUUL2dNQI5M