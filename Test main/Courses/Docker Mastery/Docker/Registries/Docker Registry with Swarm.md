```bash
multipass launch -n node1 --cloud-init docker.yaml
multipass launch -n node2 --cloud-init docker.yaml
multipass launch -n node3 --cloud-init docker.yaml
multipass launch -n node4 --cloud-init docker.yaml
multipass launch -n node5 --cloud-init docker.yaml

#multipass shell node1:$ 
docker swarm init

#copy join command:
docker swarm join --token SWMTKN-1-3wwx5tl0vmbe98em6jf70glnfboa4v3a4oomx6hc3en49zclvi-21acwhafhr8hsvupmfpvbnjn5 10.11.160.157:2377

#Add it to node12345(manager):$
docker swarm join --token SWMTKN-1-3wwx5tl0vmbe98em6jf70glnfboa4v3a4oomx6hc3en49zclvi-21acwhafhr8hsvupmfpvbnjn5 10.11.160.157:2377

docker node ls

docker service create --name registry --publish 5000:5000 registry

docker service ps registry

docker pull hello-world
docker tag hello-world 127.0.0.1:5000/hello-world

docker push 127.0.0.1:5000/hello-world

#check the repo on browser at /v2/_catalog

docker pull nginx
docker tag nginx 127.0.0.1:5000/nginx
docker push 127.0.0.1:5000/nginx

#check the repo on browser at /v2/_catalog

docker service create --name nginx -p 80:80 --replicas 5 --detach=false 127.0.0.1:5000/nginx

docker service ps nginx
```
