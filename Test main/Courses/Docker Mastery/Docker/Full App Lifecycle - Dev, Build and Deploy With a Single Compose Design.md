- Live The Dream!
- Single set of Compose files for:
- Local `docker-compose up` development environment
- Remote `docker-compose up` CI enviroment
- Remote `docker stack deploy` production enviroment

Use swarm-stack-3 files:

Test environment:
```bash
docker-compose -f docker-compose.yml -f docker-compose.test.yml up -d
```
Production environmnet:
```bash
docker-compose -f docker-compose.yml -f docker-compose.prod.yml config

```