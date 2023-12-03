- Use different Linux distro containers to check curl cli tool version

CLI Testing (--rm Automatically remove the container when it exits)
```bash
docker container run --rm -it centos:7 bash
yum update curl
curl --version

docker container run --rm -it ubuntu:14.04 bash
apt-get update && apt-get install -y curl
curl --version
```