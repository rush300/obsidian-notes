- Using Docker's Distributed Voting App
- use swarm-app-1 directory in our course repo for requirements
- 1 volume, 2 networks, and 5 services needed
- Create the commands needed, spin up services, and test app
- Everything is using Docker Hub images, so no data needed on Swarm
- Like many computer things, this is 1/2 art form and 1/2 science

# Assignment: Create A Multi-Service Multi-Node Web App

## Goal: create networks, volumes, and services for a web-based "cats vs. dogs" voting app

Here is a basic diagram of how the 5 services will work:

![diagram](./architecture.png)

- All images are on Docker Hub, so you should use editor to craft your commands locally,
then paste them into swarm shell (at least that's how I'd do it)
- a `backend` and `frontend` overlay network are needed.
Nothing different about them other than that backend will help protect database from the voting web app.
(similar to how a VLAN setup might be in traditional architecture)
- The database server should use a named volume for preserving data.
Use the new `--mount` format to do this: `--mount type=volume,source=db-data,target=/var/lib/postgresql/data`

### Services (names below should be service names)

- vote
  - bretfisher/examplevotingapp_vote
  - web frontend for users to vote dog/cat
  - ideally published on TCP 80. Container listens on 80
  - on frontend network
  - 2+ replicas of this container

- redis
  - redis:3.2
  - key-value storage for incoming votes
  - no public ports
  - on frontend network
  - 1 replica NOTE VIDEO SAYS TWO BUT ONLY ONE NEEDED

- worker
  - bretfisher/examplevotingapp_worker
  - backend processor of redis and storing results in postgres
  - no public ports
  - on frontend and backend networks
  - 1 replica

- db
  - postgres:9.4
  - one named volume needed, pointing to /var/lib/postgresql/data
  - on backend network
  - 1 replica
  - remember set env for password-less connections -e POSTGRES_HOST_AUTH_METHOD=trust

- result
  - bretfisher/examplevotingapp_result
  - web app that shows results
  - runs on high port since just for admins (lets imagine)
  - so run on a high port of your choosing (I choose 5001), container listens on 80
  - on backend network
  - 1 replica
# Answers
Work in node1

```bash
docker network create -d overlay backend
docker network create -d overlay frontend

docker service create --name vote -p 80:80 --network frontend --replicas 2 dockersamples/examplevotingapp_vote:before

docker service create --name redis --network frontend redis:3.2

docker service create --name worker --network frontend --network backend dockersamples/examplevotingapp_worker

docker service create --name db --network backend --mount type=volume,source=db-data,target=/var/lib/postgresql/data

docker service create --name result --network backend -p 5001:80 dockersamples/examplevotingapp_result:before

docker service ls
docker service ps redis
docker service ps db
docker service ps workr

docker service logs worker

```