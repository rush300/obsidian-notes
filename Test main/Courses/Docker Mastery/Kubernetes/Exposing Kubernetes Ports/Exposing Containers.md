
- `kubectl expose` creates a service for existing pods
- A service is a stable address for pod(s)
- If we want to connect to pod(s), we need a service
- CoreDNS allows us to resolve services by name
- There are different types of services
	- ClusterIP
	- NodePort
	- LoadBalancer
	- ExternalName

### Basic Service Types

- ClusterIP (default)
	- Single, internal virtual IP allocated
	- Only reachable from within cluster (nodes and pods)
	- Pods can reach service on apps port number
- NodePort
	- High port allocated on each node
	- Port is open on every node's IP
	- Anyone can connect (if they can reach node)
	- other pods need to be updated to this port
	These services are always available in Kubernetes
- LoadBalancer
	- Controls a LB endpoint external to the cluster
	- Only available when infra provider gives you a LB (AWS ELB, etc)
	- Creates NodePort+ClusterIP services, tells LB to send to NodePort
- ExternalName
	- Adds CNAME DNS record to CoreDNS only
	- Not used for Pods, but for giving pods a DNS name to use for something outside Kubernetes
- Kubernetes ingress: We'll learn later