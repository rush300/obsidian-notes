
- If you're on Docker Desktop, it provides a build-in LoadBalancer that publishes the --port on localhost
	- `kubectl expose deployment/httpenv --port 8888 --name httpenv-lb --type LoadBalancer`
	- `curl localhost:8888`
	- `kubectl get services`
- If you're on kubeadm, minikube, or microk8s
	- No built-in LB
	- You can still run the command, it'll just stay at "pending" (but its NodePort works)

## Cleanup

- Let's remove the Services and Deployment
	- `kubectl delete service/httpenv service/httpenv-np`
	- `kubectl delete service/httpenv-lb deployment/httpenv`