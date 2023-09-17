>SSRF is a vulnerability class that occurs when an application is fetching a remote resource without first validating the user-supplied URL.

==SSRF Types==
* Regular / In Band
	The response is returned in the application itself
* Blind / Out of Band
	Prove with Burp collaborator

==SSRF Impact==
* Leads to RCE
* Sensitive information disclosure
* scan of internal network
* compromise of internal services
* etc.

## Black-box Testing Perspective
 
==Map the application==
* identify any request parameters that contains host-name,  IP addresses or URL's
* For each request parameter, modify its value to specify an alternative resource and observe how the application responds
	* If a defense is in place, attempt to circumvent it using known techniques.
* *Blind/Out-of-band*. For each request parameter, modify its value to a server on the internet that you control and monitor the server for incoming requests
	* if no incoming connections are received, monitor the time taken for the application to respond

## White-box Testing Perspective

* Review source code and identify all request parameters that accept URL's
	* This could be done by combining both a black-box and withe-box testing perspective
* Determine what URL parser is being used and if it can be bypassed. Similarly determine what additional defenses are put in place that can be bypassed.

> [!IMPORTANT]- A New Era of SSRF
> Exploiting URL Parser in Trending Programming Languages by Orange Tsai
> 
![[us-17-Tsai-A-New-Era-Of-SSRF-Exploiting-URL-Parser-In-Trending-Programming-Languages.pdf]]

## Exploit Regular/In-Band SSRF

* If the application allows for user-supplied arbitrary URL's, try the following attacks:
	+ Determine if a port number can be specified
	+ If successful, attempt to port-scan the internal network using Burp Intruder
	+ Attempt to connect to other services on the loop-back address 127.0.0.1
	+ --- 
	+ **If the application does not allow for arbitrary user-supplied URLs, try to bypass defenses using the following techniques:**
		+ Use different encoding schemes
			+ decimal-encoded version of 127.0.0.1 is 2130706433
			+ 127.1 resolves to 127.0.0.1
			+ Octal representation of 127.0.0.1 is 017700000001
		* Register a domain name that resolves to internal IP address (DNS Rebinding)
		* Use your own server that redirects to an internal IP address (HTTP Rebinding)
		* Exploit inconsistencies in URL parsing
			* A New Era of SSRF!

## Exploit Blind/Out-of-Band SSRF

* If the application is vulnerable to blind SSRF, try to exploit the vulnerability using the following techniques:
	* Attempt to trigger an HTTP request to an external system you control and monitor the system for network interactions from the vulnerable server
		* Can be done using Burp Collaborator
	* If defenses are put in place, use the techniques mentioned in the previous slides to obfuscate the external malicious domain.
	* Once you're proved that the application is vulnerable to blind SSRF, you need to determine what your end goal is.
		* An example would be to probe for other vulnerabilities on the server itself or other backend systems.


> [!IMPORTANT] Cracking the Lens:
> Targeting HTTP's Hidden Attack-surface
> https://portswigger.net/research/cracking-the-lens-targeting-https-hidden-attack-surface

## Preventing SSRF Vulnerabilities

==Defense in depth approach:==
* Application Layer defenses
* Network Layer Defenses
* Sanitize and validate all client-supplied input data


