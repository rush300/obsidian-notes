```bash
#Run the registry image
docker container run -d -p 5000:5000 --name registry registry

docker pull hello-world
docker run hello-world

#Re-tag an existing image and push it to your new registry
docker tag hello-world 127.0.0.1:5000/hello-world
docker push 127.0.0.1:5000/hello-world

#Remove that image from local cache and pull it from new registry
docker image remove hello-world
docker image remove 127.0.0.1:5000/hello-world
docker pull 127.0.0.1:5000/hello-world

docker container rm regestry

#Re-create registry using a bind mount and see how it stores data
docker container run -d -p 5000:5000 --name registry -v $(pwd)/registry-data:/var/lib/registry registry

ll registry-data
docker image ls
docker push 127.0.0.1:5000/hello-world
ll registry-data

#Shows dirs and files visually
apt install tree
tree registry-data

```