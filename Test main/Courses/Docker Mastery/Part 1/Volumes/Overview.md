```bash
docker volume ls

docker volume inspect 91d3e94cb9e4a2c49e18f192507707fe3d108a33df891b05750ab0e9dbf3f989

# -v is the volume for the container, could be new or existing
# mysql-db: -> is the volume name
docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysql

docker volume ls

docker volume inspect mysql-db

docker container rm -f mysql

docker volume rm mysql-db
```
## Create
```bash
docker volume create --help
```

## Shell Differences for Path Expansion

In the next lecture, you'll learn how to share files and directories between a host and a Docker container. One of the parts of the command line you'll need to type is the host file path you want to share.

With Docker CLI, you can always use a full file path on any OS, but often you'll see me and others use a "parameter expansion" like `$(pwd)` which means "print working directory".

**Here's the important part. Each shell may do this differently,** so here's a cheat sheet for which OS and Shell your using. I'll be using $(pwd) on a Mac, **but yours may be different!**

This isn't a Docker thing, it's a Shell thing.

For PowerShell use: `${pwd}` 

For cmd.exe "Command Prompt use: `%cd%`

Linux/macOS bash, sh, zsh, and Windows Docker Toolbox Quickstart Terminal use: `$(pwd)` 

Note, if you have spaces in your path, you'll usually need to quote the whole path in the docker command.