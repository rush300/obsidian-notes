- Kubernetes = popular container orchestrator
- Container Orchestration = Make many servers act like one
- Runs on top of Docker (usually) as a set of APIs in containers
- Provides API/CLI to manage containers across servers

## Basic Terms
### System Parts

- **Kubernetes**: The whole orchestration system
	- K8s or Kube for short
- **Kubectl**: CLI to configure Kubernetes and manage apps
	- Using "cube control" official pronunciation
- **Node**: Single server in the Kubernetes cluster
- **Kubelet**: Kubernetes agent running on nodes
- **Control Plane**: Set of containers that manage the cluster
	- Includes API server, scheduler, controller manager, etcd, and more
	- Sometimes called the "master"

### Kubernetes Container Abstractions

- **Pod**: one or more containers running together on one Node
	- Basic unit of deployment. Containers are always in pods
- **Controller**: For creating/updating pods and other objects
	- Many types of Controllers inc. Deployment, ReplicaSet, StatefulSet, DaemonSet, Job, CronJob, etc.
- **Service**: network endpoint to connect to a pod
- **Namespace**: Filtered group of objects in cluster
- 