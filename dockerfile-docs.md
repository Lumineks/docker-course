# Dockerfile docs

'Dockerfile.yaml' file is used to create new images and containers based on other base-images in cases when there is no suitable image in the docker registries. Should be placed in the root of the project directory.

## Structure

1. `FROM`
   Specifies base-image
2. `WORKDIR`
   Creates working directory in the image. After this command docker also runs all next comands (COPY, CMD, etc.) from specified workdir
3. `RUN`
   Runs specified command, for example - `RUN npm install`
4. `COPY`
   Copies local file in the specified image directory. Usually this is a working image directory that was created in the previous step
5. `CMD`
   Executes command after images was created. The process for docker container.
6. `EXPOSE`
   Opens cpecified port in the container

**To build docker image from Dockerfile run `docker build <path_to_Dockerfile>`**
Example if in the folder with Dockerfile - `docker build .`

### Warning

If in the project dir Dockerfile has another name, e.x. Dockerfile-dev. Use '-f' arg to point on the Dockerfile name like `docker build . -f Dockerfile-dev`

## Useful arguments to `docker build` command usage with Dockerfile

1. '-t': define custom name and tag for created image
   Example: `docker build . -t my-image:0.1.1`

## Example of NodeJs Dockerfile

```
FROM node:alpine

WORKDIR /app

EXPOSE 3000

COPY package*.json ./

RUN npm install

COPY . ./

CMD ["npm ", "run", "dev"]
```
