
- Kubernetes configuration file (YAML or JSON)
- Each file contains one or more manifests
- Each manifest describes an API object (deployment, job, secret)
- Each manifest needs four parts (root key:values in the file)
	- `apiVersion:`
	- `kind:`
	- `metadata:`
	- `spec:`
- Check git repo: udemy-docker-mastery/k8s-yaml$ pod.yml