# Docker Compose docs

## What is it

Docker Compose is a tool that helps define and share multi-container applications. To simplify - compose lets us create YAML file to define the services and with a single command run everything.

## Advantages of Docker Compose

- Declarative way to define containers (services)
- Runs entire multi-container applications with 1 commmand - `docker compose up`
- Automatically creates images based on Dockerfile of every applicaton
- Automatically creates isolated network for containers interaction
- Applies and uses built-in DNS to resolve container links by services names

## Commands

- `docker compose up`: runs multi-container app based on docker-compose.yml file
- `docker compose down`: stops multi-container app, also removes all containers with custom network.
- flag '-d': detached.
  `docker-compose up -d` will start docker-compose in a background mode.
- flag '--build'
  `docker-compose up --build` will rebuild images if app was already built and then start newer version of the application based on the updated images.

## Containers volumes

Volumes are basically folders on our machine, or in the docker host. They are used to overwrite container's folders, or to persist container's folder data, for example database data. We can say container to use external volume, so if the container stops, next time it will be up, it will get all persisted data in previously saved external volume location.

### Syntax

```
In the docker-compose.yml, in the separatae section define docker volumes, and then in the services link them where needed.
If we want to use docker-host volume, then we write just <volume_name>:<containers folder>
If we want to use our machine folder, then we have to specify path instead of volume name: <path/to/machine/folder>:<containers folder>

```

### Replace apps folders in dev mode

In case when we develop an application, we want to have 'hot-reload' container, so when we change source files, we do not want to rebuild whole image, and the restart containers.
To reach this goal, we should use volumes, and replace in-containers app folder with our local app folder.

```
services:
  frontend:
    build: ./frontend
    volumes:
      <!-- If we want to some files persist while replacing everything else, we should define them before local volume mapping  -->
      - /app/node_modules
      - ./frontend:/app
      <!-- Where './frontend' - our local machine folder, and '/app' - container's app folder -->
```

services:
...
mysql:
image: mysql
...
volumes: - mysql_data:/var/lib/mysql

<!-- Where 'mysql_data' is the docekr volume name specified below  -->
<!-- And '/var/lib/mysql' is internal containers folder -->
<!-- So we say that container's '/var/lib/mysql' folder will read/write data defined in 'mysql_data' volume -->

...

volumes:
mysql_data:

```

## Example of docker-compose.yml

```

version: '3'

services:
  app: <!-- Service(container) name -->
    build: ./app <!-- Build custom image from Dockerfile in specified location -->
    mongo: <!-- Service(container) name -->
    image: mongo <!-- Image name -->
    restart: always
    ports:
      - 8888:3000
    depends_on:
      - mysql

```

```
