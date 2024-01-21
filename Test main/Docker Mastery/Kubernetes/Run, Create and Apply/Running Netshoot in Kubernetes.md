In the past video, "Creating a ClusterIP Service", I used the [cURL utility](https://curl.se/) to return HTTP from some containers we created to test that they work behind a Service IP. I used a `kubectl run` command to start my "bretfisher/netshoot" container image like this:

`kubectl run tmp-shell --rm -it --image bretfisher/netshoot -- bash`

The point of the video was creating and testing a Service, not "running shells in pods" or netshoot itself, so I thought I'd spell some of those details here, since you may be curious about some of the skipped detailed.

#### Running a shell in Kubernetes pods

Since version 1.18, the `kubectl run` command only creates a single pod, with a single container from a single image. Here's what `--help` says about the run command format:

`kubectl run NAME --image=image [--env="key=value"] [--port=port] [--dry-run=server|client] [--overrides=inline-json] [--command] -- [COMMAND] [args...] [options]`

**Man, that's confusing,** and it took me a while to understand all the parts of that:

1. `kubectl run NAME`: that's the easy part. The run command requires a name. It also requires an image to create the container from. Name and image are the only two required parts of a `run` command.
    
2. `--rm`: Like `docker run`, it will delete the pod after it exits.
    
3. `-it`: Like `docker run`, this is shorthand for two different options. They can exist together because the short version of each option only requires one dash, and like docker and many other Linux commands, single-letter options can be combined in a shorthand. `-i` is short for `--stdin=true` and keeps the input connection open between your shell and the container (so we can type multiple commands like curl without having to start a new container.) `-t` is short for `--tty=true` and allocates a virtual terminal for us to use in the container (which we run a bash shell in that tty).  We often use these two options together when we want a shell inside a container (via `run`, `exec`, etc.)
    
4. `--image`: The container image we want to start the container from. It's required in a `run` command.
    
5. `-- [COMMAND] [args...] [options]`: This is the tricky part. The double-dash is a common shell way for tools "to signify the end of command options, after which only positional arguments are accepted." In this case the double-dash separates the kubectl CLI options and allows us to overwrite the Dockerfile CMD with a new command and arguments/options.  Unlike docker run, kubectl run requires the double-dash to override the command. You can also just use `--command` rather than the double dash, but I tend to prefer the double-dash method because it's used in many other areas of Linux shells and it also doesn't require me to quote the whole command I want to override.
    

#### What is bretfisher/netshoot?

A colleague, Nicola Kabar, created a popular tool years ago called netshoot, which was nothing more than a container image full of common Linux utilities that are good for troubleshooting Linux, Docker, and Kubernetes, and particularly networking. Hence, "netshoot" as in Network Troubleshooting.

I forked that project, and added some of my own tools, which you can find here: [bretfisher/netshoot](https://github.com/bretfisher/netshoot)

It runs a zsh shell as the default CMD, but in the previous lecture, I had us run bash instead, just as a learning example.