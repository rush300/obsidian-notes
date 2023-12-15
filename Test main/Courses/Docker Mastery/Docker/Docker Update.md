```bash
docker service create -p 8088:80 --name web nginx:1.13.7
docker service ls
docker service scale web=5
docker service update --image nginx:1.13.6 web
docker service update --publish-rm 8088 --publish-add 9090:80
docker service update --force web
docker service rm web
```