==Consistently== build, run and ship applications.
```bash
sudo service docker start - Kali
sudo systemctl start docker - Ubuntu
docker-compose up
docker-compose down --rmi all
```
## Package an application
Use Visual Studio Code
```bash
vi app.js
vi Dockerfile
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js
:wq!

docker build -t hello-docker .
docker images
docker run hello-docker
docker version
docker pull image
docker image ls

docker run -it ubuntu
```