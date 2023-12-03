- Know how to use -it to get shell in container
- Understand basics of DNS records

This exercise simulate load-balancer.
```bash
docker network create dude

docker container run -d --net dude --net-alias search elasticsearch:2

docker container run -d --net dude --net-alias search elasticsearch:2

docker container ls

docker container run --rm --net dude alpine nslookup search

#Return random container each time was called
docker container run --rm --net dude centos curl -s search:9200

docker container rm -f containerName1 containerName2
```
