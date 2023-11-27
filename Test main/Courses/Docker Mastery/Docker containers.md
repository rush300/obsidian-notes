- docs.docker.com and --help are your friend

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
```