
- These commands use helper templates called "generators"
- Every resource in Kubernetes has a specification or "spec"
	- `kubectl create deployment sample --image nginx --dry-run=client -o yaml`
- You can output those templates with --dry-run=client -o yaml
- You can use those YAML defaults as a starting point
- Generators are "opinionated defaults"

## Generator Examples

- Using dry-run with yaml output we can see the generators
	- `kubectl create deployment test --image nginx --dry-run=client -o yaml`
	- `kubectl create job test --image nginx --dry-run=client -o yaml`
	- `kubectl expose deployment/test --port 80 --dry-run=client -o yaml`
		- You need the deployment to exist before this works
	- `kubectl create deployment test --image nginx`

## Cleanup

- Let's remove the Deployment
	- `kubectl delete deployment test`