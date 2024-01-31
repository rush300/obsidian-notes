
- Let's expose a NodePort so we can access it via the host IP (including localhost on Windows/Linux/macOS)
	- `kubectl expose deployment/httpenv --port 8888 --name httpenv-np --type NodePort`
	- `kubectl get services`
- Did you know that a NodePort service also creates a ClusterIP?
- These three service types are additive, each one creates the ones above it:
	- ClusterIP
	- NodePort
	- LoadBalancer