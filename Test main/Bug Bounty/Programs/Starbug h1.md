# IDOR Testing

## Pointers

1. CSRF Token doesn't appear to be used with GET request to '/rewards/Profile'
2. Session token ( 'auth=dkasdkasjdkas' ) does not have HTTP Only flag
3. Post Request to update User Object at https://www.starbucks.com.sg/rewards/Profile must include Email param in body but doesn't seem to validate it
4. JWT using Symetric Encryption w/ HS256
5. Unique cookies on some endpoints but not others: `performace-cookie=on; cookie-accepted=true`
## Accounts

rusec+demo1@wearehackerone.com

JWT TOKEN

rusec+demo2@wearehackerone.com

JWT TOKEN

#### Steps
1. Login with demo1
2. Start Burp and proxy the traffic
3. Add scope starbugs (Scope settings/add/yes/Show only in-scope items/Apply)
4. Check Wappalyzer browser extension
5. Go to Profile page and forward request to repeater in burp
6. 

## Mechanisms

### Gift Card

READ = POST -> `/rewards/api/card/search?`
- Through `ACCESS_TOKEN` cookie (JWT w/ HS256)
- Signature being validated
- Test JWT vulnerabilities 

READ = POST -> `/rewards/api/card/detail?`
- JSON body: `{"cardNo":"0423253598787"}`
- Through `ACCESS_TOKEN` cookie (JWT w/ HS256)
- Signature being validated
- Test JWT vulnerabilities 


CREATE = POST -> `/rewards/Cards/Add`
- Through `auth` cookie
### Personal Information

READ = GET -> `/rewards/profile`
- Through `auth` cookie

UPDATE = POST -> `/rewards/profile`
- Through `auth` cookie?
- Fuzz for hidden parameters

UPDATE = POST -> `/rewards/Profile/ChangeEmail`
- Through `auth` cookie?
- Fuzz for hidden parameters
### Payment Methods

READ = GET -> `/rewards/api/card/get-payment-cards`
- Through `ACCESS_TOKEN` cookie (JWT w/ HS256)
- Signature being validated
- Test JWT vulnerabilities 

CREATE = POST -> `/rewards/api/card/amex-save-payment-card-on-web`
	- No data access/modification, simply hadles redirect
## Objects

### User Object
```
Paste user object from `/rewards/profile` by Update in the request body
```

### Gift Card

```
Paste card object from `/rewards/api/card/search?` in the response body
```

### Payment Card Object

Must add legit card, added through external service
### Transaction

```
"transactionId": "a4liw4gia4gal4gwailg4awif4twfatdpuhsto"
```
