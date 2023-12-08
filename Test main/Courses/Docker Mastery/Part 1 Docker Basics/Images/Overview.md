## What's In an Image
- App binaries and dependencies
- Metadata about the image data and how to run the image
- Not a complete OS. No kernel, kernel modules (e.g. drivers)
- Small as one file (your app binary) like a golang static binary
- Big as a Ubuntu distro with apt, and Apache, PHP, and more installed

## Hub Registry
- Basics of Docker Hub (hub.docker.com)
- Find Official and other good public images

## Images Layers
```bash
docker image ls

#Shows all the layers in the image
docker history nginx:latest
```

## Pushing to docker hub

``<user>/<repo>:<tag>``
```bash
docker image tag --help

#Rename image
docker image tag nginx rusev/nginx

docker image ls

docker image push rusev/nginx #-> have to be logged in

docker login

cat .docker/config.json #Check authentication key
```
## Using Prune to Keep Your Docker System Clean (YouTube)

You can use "prune" commands to clean up images, volumes, build cache, and containers. Examples include:

- `docker image prune` to clean up just "dangling" images

- `docker system prune` will clean up everything you're not currently using

- The big one is usually `docker image prune -a` which will remove all images you're not using. Use `docker system df` to see space usage.

Remember each one of those commands has options you can learn with `--help`.

Here's a YouTube video I made about it: [https://youtu.be/_4QzP7uwtvI](https://youtu.be/_4QzP7uwtvI)

Lastly, realize that the Linux VM will *eventually* auto-shrink. You may not see the free space on your host OS right away, and it may take Docker a restart and some idle time before it completes a VM shrink.