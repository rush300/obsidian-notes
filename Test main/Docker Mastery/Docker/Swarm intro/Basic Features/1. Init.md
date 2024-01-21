```bash
docker swarm init
docker node ls
docker node --help
docker swarm --help
docker service --help

docker service create alpine ping 8.8.8.8
docker service ls
docker service ps <serivice-name>

docker service update <service-ID> --replicas 3
docker service ls
docker service ps <service-name>

docker update --help
docker service update --help

docker container ls
docker container rm -f <service-name>.1.<ID>
docker service ls
docker service ps <service-name> 
docker service ls
```
