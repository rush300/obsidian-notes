Docker labs web
https://labs.play-with-docker.com/

Docker hub
https://hub.docker.com/

```bash
#run appache web server on port 80. Host Port 8800
docker run -d -p 8800:80 httpd
curl localhost:8800
docker ps

```