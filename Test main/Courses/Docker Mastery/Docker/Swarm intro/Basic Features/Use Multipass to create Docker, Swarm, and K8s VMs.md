**You'll hear me talking about Docker Machine in various lectures. Docker has stopped support for docker-machine**, and we mostly have better tools for this now.

#### Use Multipass as a better option for managing multiple local VMs

If you'd like to create multiple VM's for setting up Swarm or K8s clusters, use [multipass.run](https://multipass.run)

Multipass creates full Ubuntu server VM on your Host machine using various virtualization options (hyper-v, VirtualBox, hyperkit, etc.). It's super fast to create one and easy to use.  Their [website has a quick walkthrough](https://multipass.run) for each host OS type.

Once you have Multipass VM's created, then install docker and/or kubernetes inside them (`multipass shell <name>` gets you into the VM shell, `multipass mount` can connect a host directory into the VM, and `multipass transfer` can copy files in.)

#### Background on Docker Machine depreciation

docker-machine which was used to create VMs with docker pre-installed. The last release from 2019 is archived on [github](https://github.com/docker/machine/releases/tag/v0.16.2). There isn't anything wrong with docker machine, Docker simply shifted focus from creating virtual machines. Today there are better alternatives like [multipass](https://multipass.run/). For the course, you can still choose to use docker-machine but multipass is the best option. You can see me discuss multipass on my [live show](https://www.pscp.tv/BretFisher/1mrGmQvNEWBGy).