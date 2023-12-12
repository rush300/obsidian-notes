- A. play-with-docker.com
	- Only needs a browser, but reset after 4 hours
- Use multipass provisioning!

use get.docker.com
```bash
multipass launch -n node1 --cloud-init docker.yaml
multipass launch -n node2 --cloud-init docker.yaml
multipass launch -n node3 --cloud-init docker.yaml

#multipass shell node1:$ 
docker swarm init

#copy join command:
docker swarm join --token SWMTKN-1-3wwx5tl0vmbe98em6jf70glnfboa4v3a4oomx6hc3en49zclvi-21acwhafhr8hsvupmfpvbnjn5 10.11.160.157:2377

#Add it to node2(worker):$
docker swarm join --token SWMTKN-1-3wwx5tl0vmbe98em6jf70glnfboa4v3a4oomx6hc3en49zclvi-21acwhafhr8hsvupmfpvbnjn5 10.11.160.157:2377

#node1:$ 
docker node ls
#(Promote node2 to manager)
#node1:$ 
docker node update --role manger node2
#node1:$ 
docker node ls
#node1:$ 
docker swarm join-token manager

#copy join command:
docker swarm join --token SWMTKN-1-3wwx5tl0vmbe98em6jf70glnfboa4v3a4oomx6hc3en49zclvi-052101xqroxuopsa77zfnfzvc 10.11.160.157:2377

#Add it to node3(leader):$
docker swarm join --token SWMTKN-1-3wwx5tl0vmbe98em6jf70glnfboa4v3a4oomx6hc3en49zclvi-052101xqroxuopsa77zfnfzvc 10.11.160.157:2377

#node1:$ 
docker service create --replicas 3 alpine ping 8.8.8.8
#node1:$ 
docker service ls
#node2:$ 
docker service ls
#node3:$ 
docker service ls
#node1:$ 
sudo docker node ps node2
#node1:$ 
docker service ps <service-name>

#node1:$ 
docker service scale <service-name>=5
#node1:$ 
docker service ps <service-name>

```

docker.yaml -> 
```yml
runcmd:
  - 'curl -sSL https://get.docker.com/ | VERSION=19.03.8 sh'
  - 'usermod -aG docker ubuntu'
```
