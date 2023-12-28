- Open two shell windows so we can watch this
	- `kubectl get pods -w`
- In second window, lets start a simple http server using sample code
	- `kubectl create deployment httpenv --image=bretfisher/httpenv
- Scale it to 5 replicas
	- `kubectl scale deployment/httpenv --replicas=5`
- Let's create a ClusterIP service (default)
	- `kubectl expose deployment/httpenv --port 8888`
- Verify our service was created
	- `kubectl get service`

## cURL the ClusterIP Service

- Remember this IP is cluster internal only, how do we curl it?
- Create a Pod and connect to shell *in* the cluster
	- `kubectl run tmp-shell --rm -it --image bretfisher/netshoot -- bash`
	- curl httpenv:8888

## Cleanup

- Leave the deployment there, we'll use it in the next Lecture