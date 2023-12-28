
Did you know that internal cluster DNS isn't a "mandatory required feature" of Kubernetes? Yea, it's kinda wired that it's not required like the other parts (etcd, API, scheduler, controller manager, and kubelet).

The standard DNS used in Kubernetes is the [CoreDNS project](https://coredns.io), and is _usually_ installed as part of your Kubernetes distribution because you can't use Kubernetes Service resources without it. In order to talk from one Pod to another pod, you usually need a Service endpoint, and that requires friendly DNS names, which require CoreDNS to resolve inside the cluster network. **Services are used in every cluster I've seen, so I consider CoreDNS a required service in any Kubernetes.**

However, MicroK8s tries to be as minimal as possible on a default install (hence the name), requiring one extra step to install CoreDNS. **If you're using MicroK8s, you'll need to enable DNS now in order to continue with this course:**

`microk8s enable dns`

To check the status of all features/add-in's in MicroK8s:

`microk8s status`

For more MicroK8s info, there's the [getting started guide](https://microk8s.io/docs/getting-started), and the [command reference](https://microk8s.io/docs/command-reference).