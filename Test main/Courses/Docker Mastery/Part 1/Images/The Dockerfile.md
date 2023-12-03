## Basics
.Dockerfile

#This is a sample Image 
FROM ubuntu 
MAINTAINER demousr@gmail.com 

RUN apt-get update 
RUN apt-get install –y nginx 
CMD [“echo”,”Image created”]

```bash
docker image build -t customnginx .

docker image ls

#Change the file and rebuild
docker image build -t customnginx .
```
## Extending Official Images

```bash
/workdir# ls
Dockerfile
index.html
```
```dockerfile
FROM nginx:latest

WORKDIR /usr/share/nginx/html

COPY index.html index.html
```
```bash
#Original image index.html
docker container run -p 80:80 --rm nginx

#Buold image with custom index.html
docker image build -t nginx-with-html .
```

## Build Your Own Dockerfile and run Containers From it

```Dockerfile
#you should use the 'node' official image, with the alpine 6.x branch
FROM node:6-alpine
#so it will respond to http://localhost:80 on your computer
EXPOSE 3000
#then it should use alpie package manager to install tini: 'apk add --update tini'
RUN apk add --update tini
#then it should create directory /usr/src/app for app files with 'mkdir -p /usr/src/app'
RUN mkdir -p /usr/src/app
#Node uses a "package manager", so it needs to copy in package.json file
WORKDIR /usr/src/app
COPY package.json package.json
#then it needs to run 'npm install' to install dependencies from that file
RUN npm install && npm cache clean
#then it needs to copy in all files from current directory
COPY . .
#then it needs to start container with command 'tini -- node ./bin/www'
CMD ["tini", "--", "node", "./bin/www"]
```

```bash
docker build -t testnode .
docker container run --rm -p 80:3000 testnode

#Rename image
docker tag testnode rush300/testing-node

docker push rush300/testing-node

#Remove image loacally
docker image rm rush300/testing-node

docker container run --rm -p 80:3000 rush300/testing-node
```