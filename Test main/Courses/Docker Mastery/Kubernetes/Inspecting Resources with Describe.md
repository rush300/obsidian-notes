- kubectl get has a weakness
	- It can only show one resource at a time
- We need a command that combines related resources
	- Parent/child resouces
	- Events of that resource

`kubectl describe deploy/my-apache`
- Deployment summary
- ReplicaSet status
- Pod template
- Old/New ReplicaSet names
- Deployment Events

- Show details about a pod, including events
	- `kubectl describe pod/my-apache-xxxx-yyyy`

```bash
kubectl get pods

kubectl describe pod/my-apache-86c695c9b5-2vv9f
```

## Inspecting Nodes

- A typical workflow of "high level" to "low level" details
- List all our clusters nodes
	- `kubectl get nodes`
- List just our node, with more details
	- `kubectl get node docker-desktop -o wide`
- Describe the node
	- `kubectl describe node/docker-desktop`

## Watching Resources

- Current commands give us a point-in-time status
- On Linux. we might use a `watch kubectl get pods` command
- But kubectl has -w (--watch) built-in!
	- `kubectl get pods`
	- `kubectl get pods -w`
- In a separate tab/window
	- `kubectl delete pod/my-apache-xxxx-yyyy` 
	- Watch the pod get re-created
- See all recent events
	- `kubectl get events`
- Watch for only future events
	- `kubectl get events --watch-only`

## Container Logs in Kubernetes

- Get a container's logs (picks a random replica, first container only)
	- `kubectl logs deploy/my-apache`
- Follow new log entries, and start with the latest log line
	- `kubectl logs deploy/my-apache --follow --tail 1`
- Get a specific container's logs in a pod
	- `kubectl logs pod/my-apache-xxx-yyy -c httpd`
- Get logs of all containers in a pod
	- `kubectl logs pod/my-apache --all-containers=true`
- Get multiple pods logs
	- `kubectl logs -l app=my-appache`
- Checkout github.com/stern/stern

Delete my-apache deployment
`kubectl delete deployment my-apache`