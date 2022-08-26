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

1. `-i`: interactive mode
2. `-t`: terminal
   Combination: `-it`
   To enter started container, should use both -i and -t flags -> this combination will not pause container but open it's CLI in current terminal

### Example: `docker run busybox -it`

3. `-d`: detached
   With this flag container will be started in a background mode, without blocking active
4. `-p <pc_port>:<container_port>`: publish
   Example: docker run -p 8080:80 nginx - maps current pc '8080' port to cotainers '80' port
5. `-v <local_folder>:<container_folder>`: volume
   Replaces specified container folder with specified local one
   As a little helper we can use ${PWD} cross OS variable that inserts path to the current terminal folder

### Example: `docker run -v ${PWD}:/usr/share/nginx/html -p 8080:80 -d nginx`

6. `--rm`: remove
   Removes container after stop

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

## `docker exec <flags> <container_name | container_id> <process_name>`

Executes proccess in active container

## `docker stop <container_id | container_name>`

Stops active container

## `docker kill <container_id | container_name>`

Kills active container proccess, should use if 'stop' command does not work

## `docker pull <image-name>`

Downloads and saves image from docker hub
// Makes sense to use `docker run`, as this command downloads remote image automatically

## `docker rm <container_id> | <container_name>`

Removes existing started/stopped container by id/name

## `docker container prune`

Removes all stopped containers

## `docker inspect <container_id> or <container_name>`

Shows details of a particular container

Details filter: `| grep <property_name>`
Example: `docker inspect <id> grep IPAddress` - will show only ip-address related info

## Command break-lines

Use `\` to break line in a docker command

### Example:

```
docker run \
--name my-nginx-container \
-v ${PWD}:/usr/share/nginx/html \
-p 8088:80 \
-d \
--rm \
nginx
```
