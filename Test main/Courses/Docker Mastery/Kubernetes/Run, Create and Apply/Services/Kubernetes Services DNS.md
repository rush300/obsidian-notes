
- Starting with 1.11, internal DNS is provided by CoreDNS
- Like Swarm, this is DNS-Based Service Discovery
- So far we've been using hostnames to access Services
	- `curl <hostname>`
- But that only works for Services in the same Namespace
	- `kubectl get namespaces`
- Services also have a FQDN
	- `curl <hostname>.<namespace>.svc.cluster.local`
	- 