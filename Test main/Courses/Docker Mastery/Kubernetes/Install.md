
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

## Kubespray with multipass

### Multipass
```bash
sudo snap install multipass
```
#### How to launch LTS instances

The first five minutes with Multipass let you know how easy it is to have a lightweight cloud handy. Let’s launch a few LTS instances, list them, exec a command, use cloud-init and clean up old instances to start.

Launch an instance (by default you get the current Ubuntu LTS)
```
multipass launch --name foo
```
Run commands in that instance, try running bash (logout or ctrl-d to quit)
```
multipass exec foo -- lsb_release -a
```
See your instances
```
multipass list
```
Stop and start instances
```
multipass stop foo bar
```
```
multipass start foo
```
Clean up what you don’t need
```
multipass delete bar
```
```
multipass purge
```
Find alternate images to launch
```
multipass find
```

##### Install cluster with 5 nodes(VMs)

- 3 masters k8s-master-1,2,3
- 2 workers k8s-worker-1,2
- 1 console  k8s-console

### Install Kubespray

```
multipass launch k8s-console

git clone https://github.com/kubernetes-sigs/kubespray.git

cd ~/.ssh

ssh-keygen

python3 -m http.server
```
Copy id_rsa.pub into other MVs master-1,2,3 and worker-1,2
```
curl http://(k8s-console)IP:Port/id_rsa.pub > ~/.ssh/id_rsa.pub
cat id_rsa.pub >> authorized_keys
```
Try ssh from k8s-console to other machines
```
ssh (master-1)ubuntu@IP
```

#### Installing Ansible

Kubespray supports multiple ansible versions and ships different `requirements.txt` files for them. Depending on your available python version you may be limited in choosing which ansible version to use.

It is recommended to deploy the ansible version used by kubespray into a python virtual environment.

```shell
VENVDIR=kubespray-venv
KUBESPRAYDIR=kubespray
python3 -m venv $VENVDIR
source $VENVDIR/bin/activate
cd $KUBESPRAYDIR
pip install -U -r requirements.txt
```
```bash
# Copy ``inventory/sample`` as ``inventory/mycluster``
cp -rfp inventory/sample inventory/mycluster

# Update Ansible inventory file with inventory builder
declare -a IPS=(10.10.1.3 10.10.1.4 10.10.1.5)
CONFIG_FILE=inventory/mycluster/hosts.yaml python3 contrib/inventory_builder/inventory.py ${IPS[@]}

# Review and change parameters under ``inventory/mycluster/group_vars``
cat inventory/mycluster/group_vars/all/all.yml
cat inventory/mycluster/group_vars/k8s_cluster/k8s-cluster.yml

# Clean up old Kubernetes cluster with Ansible Playbook - run the playbook as root
# The option `--become` is required, as for example cleaning up SSL keys in /etc/,
# uninstalling old packages and interacting with various systemd daemons.
# Without --become the playbook will fail to run!
# And be mind it will remove the current kubernetes cluster (if it's running)!
ansible-playbook -i inventory/mycluster/hosts.yaml  --become --become-user=root reset.yml

# Deploy Kubespray with Ansible Playbook - run the playbook as root
# The option `--become` is required, as for example writing SSL keys in /etc/,
# installing packages and interacting with various systemd daemons.
# Without --become the playbook will fail to run!
ansible-playbook -i inventory/mycluster/hosts.yaml  --become --become-user=root cluster.yml
```

