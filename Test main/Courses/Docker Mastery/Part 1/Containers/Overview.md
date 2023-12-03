- docs.docker.com and --help are your friend

## Basic Container commands
```bash
#Run container
docker container run --publish 80:80 nginx

#Run container in background
docker container run --publish 80:80 --detach nginx

#Run container with specific name
docker container run --publish 80:80 --detach --name webhost nginx

#Show all running containers
docker container ls

#Show all containers 
docker container ls -a

#Stop container
docker container stop bf6f.. #ID

#docker container stop use --force for running containers
docker container rm --force bf6f 012c 4e17

#Docker top lists running processes in specific container
docker top nginx

#Show container config
docker container inspect nginx

#Show containers performance
docker container stats

#Show all processes on the system
ps aux | grep nginx

#Show docker images 
docker image ls

#Show container logs
docker container logs webhost
docker container logs --follow monerod

```
```bash
docker container run -p #Expose port on local machine

docker container run -p 80:80 --name webhost -d nginx

docker container port webhost #Shows ports forwarding

docker container inspect --format '{{ .NetworkSettings.IPAddress }}' webhost #Get the IP of a container
```
### Get shell to container
```bash
docker container run -it #start new container interactively

docker container exec -it #run additional command in existing container

docker container start --help

docker container start -ai nginx #Start with console

docker container exec -it mysql bash

ps aux #Shows the processes inside a container

docker container run -it alpine bash #Error alpine is so small and doesn't have bash installed. But has sh *tiny terminal compared to bash  terminal*

docker container run -it alpine sh
```

## Networking
### CLI Management

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
### DNS
```bash
#Containers see each other only if are in custom network!
#Ping two containers in the same network
docker container exec -it my_nginx ping new_nginx
```
