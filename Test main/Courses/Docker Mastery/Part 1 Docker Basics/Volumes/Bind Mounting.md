- Maps a host file or directory to a container file or directory
- Basically just two locations pointing to the same file(s)
- Can't use in Dockerfile, must be at container run
- ... run -v /Users/rushsec/stuff:/path/container (mac/linux)
- ... run -v //c/Users/rushsec/stuff:/path/container (windows)

```bash
cd /repos/udemy-docker-mastery/dockerfile-sample-2

#Check the container volume "Mounts: Destination: /usr/share/nginx/html"
docker container inspect nginx

#Mount current host directory to the container directory
docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx

#Open the container
docker container exec -it nginx bash

root@container$ cd /usr/share/nginx/html

#Shows same dir on the container and the host
root@container$ ls -al

#Create new file on the host
touch testme.txt

#Show again the files and the new file from the host is also there
root@container$ ls -al
```