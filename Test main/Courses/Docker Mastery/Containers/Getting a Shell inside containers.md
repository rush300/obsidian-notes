```bash
docker container run -it #start new container interactively

docker container exec -it #run additional command in existing container

docker container start --help

docker container start -ai nginx #Start with console

docker container exec -it mysql bash

ps aux #Shows the processes inside a container

docker container run -it alpine bash #Error alpine is so small and doesn't have bash installed. But has sh *tiny terminal compared to bash  terminal*

docker container run -it alpine sh
```