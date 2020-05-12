# react-docker
Simple React with docker

## Create Dockerfile
- Dockerfile is the blueprint to create an image
- Explanation of what happens in a container:
-- create a node project
-- in the directory /client
-- copy the package.json file to /client
-- run npm install with this package.json file
-- copy entire content of project to the client folder
-- expose port 3000
-- run the project with npm start

```
FROM node

WORKDIR /client

COPY package*.json /client/

RUN npm install

COPY . /client/

EXPOSE 3000
CMD ["npm", "start"]
```

## Create .dockerignore
- Add the following:
```
node_modules
npm-debug.log
```

## Creating a Docker image
- build a docker image
```bash
docker build -t cc/frontend .
```
- check built docker images

```bash
docker images
```

- remove image with docker rmi <image-id>
```bash
docker rmi eaeb5
```

## Running a Docker image
- run an image with port and image name
- serves up at localhost:3000
```bash
docker run -p 3000:3000 cc/frontend
```

- see all docker containers running with `docker ps`

- stop a docker instance with `docker stop <image-id`>`
- start a docker instance with `docker start <image-id`>`

- pull an image from Docker hub with `docker pull <image-name>`
```bash
docker pull mongo
docker pull node
```

- push own repos with `docker push <image-name>`


## Reference
- Full list of [Docker commands](https://docs.docker.com/engine/reference/commandline/docker/)
