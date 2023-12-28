
### In Browser

- Try http://play-with-k8s.com or
- http://katacoda.com

### For Linux

- MicroK8s
- https://microk8s.io/#install-microk8s
	- `sudo snap install microk8s --classic`
	- `microk8s enable dashboard
	- `microk8s enable dns
	- `microk8s enable registry
	- `microk8s enable istio
	- Start and stop Kubernetes to save battery Kubernetes is a collection of system services that talk to each other all the time. If you don't need them running in the background then you will save battery by stopping them. `microk8s start` and `microk8s stop` will do the work for you.
- Add an alias to your shell (.bash_profile)
	- `alias kubectl=microk8s.kubectl` to `nano ~/.bashrc`

- Docker Desktop
```