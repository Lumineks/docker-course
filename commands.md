# terminal commands

## List of available and learnt docker commands

<br/>

## `docker version`

Shows docker client and engine versions

## `docker ps`

Shows all local started containers

## `docker ps -a`

Shows all local started/paused containers

## `docker images`

Shows local images

## `docker run <image-name>`

Creates and starts docker container from docker image

1. Docker tries to find image locally
2. If image does not exist locally - docker checks docker hub repositories, if found - downloads, saves locally and creates container from this downloaded image

### Flags
1) `-i`: interactive mode
2) `-t`: terminal
Combination: `-it`
To enter started container, should use both -i and -t flags -> this combination will not pause container but open it's CLI in current terminal
### Example: `docker run busybox -it`

### Example of official 'hello-world' image from docker hub

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
1.  The Docker client contacted the Docker daemon.
2.  The Docker daemon pulled the "hello-world" image from the Docker Hub. (amd64)
3.  The Docker daemon created a new container from that image which runs the executable that produces the output you are currently reading.
4.  The Docker daemon streamed that output to the Docker client, which sent it to your terminal.
```

## `docker pull <image-name>`

Downloads and saves image from docker hub
// Makes sense to use `docker run`, as this command downloads remote image automatically

##  `docker rm <container_id> | <container_name>`
Removes existing started/stopped container by id/name

## `docker container prune`
Removes all stopped containers