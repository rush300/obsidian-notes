- Storage and stateful workloads are harder in all systems
- Containers make it both harder and easier than before
- ==StatefulSets== is a new resource type, making Pods more sticky
- Bret's recommendation: avoid stateful workload for first few deployments until you're good at the basics
	- use db-as-a-service whenever you can

## Volumes in Kubernetes

- Creating and connecting Volumes: 2 types
- Volumes
	- Tied to lifecycle of a Pod
	- All containers in a single Pod can share them
- PersistentVolumes
	- Created at the cluster level, outlives a Pod
	- Separates storage config from Pod using it
	- Multiple Pods can share them
- CSI plugins are the new way to connect to storage