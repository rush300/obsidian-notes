[[nmap]]
[[ffuf]]

Try to signup a user:
Change method from GET to POST
path: /api/v1/user/signup

header = content-type: application/json
add body:
{
	"email": "user@me.com"
	"password": "pass1234"
}

Then try to login:
path: /api/v1/user/login

*header = content-type: application/json
add body:
{
	"username": "user@me.com"
	"password": "pass1234"
}**

*if header = content-type: application/x-www-form-urlencoded
username=user@me.com&password=pass1234*

Get access-token:
token_type: bearer = JWT token

Go to resource where Not authenticated:
path: /docs
add header = Authorization: bearer
add body = JWT token 
Forward from burp