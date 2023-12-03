- Database upgrade with containers
- Create a postgres container with named volume psql-data using version 9.6.1
- Use docker Hub to learn Volume path and versions needed to run it

- Create a new postgres container with same named volume using 9.6.2
- check logs to validate

```bash
docker volume create psql

docker run -d --name psql1 -e POSTGRES_PASSWORD=mypassword -v psql:/var/lib/postgresql/data postgres:15.1

docker logs psql1

docker stop psql1

docker run -d --name psql2 -e POSTGRES_PASSWORD=mypassword -v psql:/var/lib/postgresql/data postgres:15.2

docker logs psql2

docker stop psql2
```