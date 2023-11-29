```bash
docker container run -p #Expose port on local machine

docker container run -p 80:80 --name webhost -d nginx

docker container port webhost #Shows ports forwarding

docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost #Get the IP of a container
```
## CLI Management

Anywhere I do a `docker container run <stuff> nginx` , where `nginx`  is the image you should use, replace that with `nginx:alpine` , which still has ping command in it.

```bash
docker network ls #Show networks

docker network inspect #Inspect a network
example: docker network inspect 4f3fg43(network id)

docker network create --driver #Create a network
example: docker network create my_app_net

docker network connect #Attach a network to container

docker network disconnect #Detach a network from container

example: docker container run -d --name new_nginx --network my_app_net nginx

docker network --help

docker network connect 3a28s39..(network id) 0f2gj24..(container id) #Connect container to other network

docker network disconnect 3a28s39..(network id) 0f2gj24..(container id) #Disonnect container from  network
```
## DNS

```bash
#Containers see each other only if are in custom network!
#Ping two containers in the same network
docker container exec -it my_nginx ping new_nginx
```
