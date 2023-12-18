```bash
sudo snap install multipass


```
Don’t have the `snap` command? [Get set up for snaps](https://docs.snapcraft.io/installing-snapd)

## How to launch LTS instances

The first five minutes with Multipass let you know how easy it is to have a lightweight cloud handy. Let’s launch a few LTS instances, list them, exec a command, use cloud-init and clean up old instances to start.

Launch an instance (by default you get the current Ubuntu LTS)

```
multipass launch --name foo
```

Run commands in that instance, try running bash (logout or ctrl-d to quit)

```
multipass exec foo -- lsb_release -a
```

See your instances

```
multipass list
```

Stop and start instances

```
multipass stop foo bar
```

```
multipass start foo
```

Clean up what you don’t need

```
multipass delete bar
```

```
multipass purge
```

Find alternate images to launch

```
multipass find
```

Pass a cloud-init metadata file to an instance on launch. See [using cloud-init with multipass](https://blog.ubuntu.com/2018/04/02/using-cloud-init-with-multipass) for more details

```
multipass launch -n bar --cloud-init cloud-config.yaml
```

See your instances

```
multipass list
```

Get help

```
multipass help
```

```
multipass help <command>
```