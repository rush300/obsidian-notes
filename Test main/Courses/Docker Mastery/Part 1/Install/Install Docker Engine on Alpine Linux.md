_Docker is a popular container platform to run virtualized lightweight machines. Here we learn how to install Docker Engine and Compose on Alpine Linux using simple commands to run Containers._

Alpine Linux is popular for its lightweight, security, and performance, hence widely used for installing Docker for creating containers using various Images available on Docker Hub. If you are an Alpine user and want to know how to use this container platform on Linux, here are the steps to follow.

**On the Page** [hide](https://linux.how2shout.com/how-to-install-docker-engine-on-alpine-linux/#)

[Steps to install Docker Engine & Compose on Alpine Linux](https://linux.how2shout.com/how-to-install-docker-engine-on-alpine-linux/#Steps_to_install_Docker_Engine_Compose_on_Alpine_Linux)

[1. Run Alpine update](https://linux.how2shout.com/how-to-install-docker-engine-on-alpine-linux/#1_Run_Alpine_update)

[2. Install Docker Engine and Compose](https://linux.how2shout.com/how-to-install-docker-engine-on-alpine-linux/#2_Install_Docker_Engine_and_Compose)

[3. Start and enable Docker Service](https://linux.how2shout.com/how-to-install-docker-engine-on-alpine-linux/#3_Start_and_enable_Docker_Service)

[4. Add your Alpine user to the Docker group](https://linux.how2shout.com/how-to-install-docker-engine-on-alpine-linux/#4_Add_your_Alpine_user_to_the_Docker_group)

[5. Test Docker](https://linux.how2shout.com/how-to-install-docker-engine-on-alpine-linux/#5_Test_Docker)

## Steps to install Docker Engine & Compose on Alpine Linux

### 1. Run Alpine update

First, on the command line of this Linux, run the system update command to refresh the repository cache.

apk update

### 2. Install Docker Engine and Compose

The packages to install Docker are already in the repository of Alpine Linux, hence we don’t need to add anything. Just use the APK package manager and install the required packages.

apk add docker docker-compose

### 3. Start and enable Docker Service

By default, the Docker service is not activated to run by the system automatically with every boot. Hence we have to do that manually, here are the commands to follow.

rc-update add docker boot
service docker start

[![Enable and start Docker service on Alpine Linux](https://www.how2shout.com/linux/wp-content/uploads/2021/10/Enable-and-start-Docker-service-on-Alpine-Linux.png "Enable and start Docker service on Alpine Linux")](https://www.how2shout.com/linux/wp-content/uploads/2021/10/Enable-and-start-Docker-service-on-Alpine-Linux.png)

### 4. Add your Alpine user to the Docker group

If you are using any user other than root then you have to use sudo with every command of docker. To remove this inconvenience, you can add your system user to the Docker’s group.

addgroup username docker

### 5. Test Docker

Now, let’s test whether everything is working absolutely fine and would we be able to create containers or not. To check, here we are downloading the Ubuntu docker image to create a container for that.

docker pull ubuntu:latest

**Create container:**

docker create -t -i  --name myubuntu ubuntu:latest

**Start Container:**

docker start myubuntu

**Switch and Access the installed Ubuntu Container root user:**

docker exec -it ubuntu /bin/bash

**Stop container:**

docker stop myubuntu

**Remove container**

docker rm myubuntu

[![Test Docker on Alpine Linux](https://www.how2shout.com/linux/wp-content/uploads/2021/10/Test-Docker-on-Alpine-Linux.png "Test Docker on Alpine Linux")](https://www.how2shout.com/linux/wp-content/uploads/2021/10/Test-Docker-on-Alpine-Linux.png)