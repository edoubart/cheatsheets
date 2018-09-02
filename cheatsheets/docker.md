# Docker Cheatsheet

## Prerequisites
Install Docker Community Edition for Mac from Docker Store:

[Docker Store](https://store.docker.com/editions/community/docker-ce-desktop-mac)

## Docker
* Restart Docker daemon:
`sudo service docker restart`

* Build Docker image from `Dockerfile`:
`docker image build -t <image-name> .`

* List Docker images:
`docker image ls`

* Run Docker container and automatically remove the container after it has been stopped:
`docker container run -it --rm --name <container-name> -p <docker-host-port>:<docker-container-port> <container-name>`

In debug mode?
`docker container run -it --rm --name <container-name> -p <docker-host-port>:<docker-container-port> -e NODE_DEBUG=1 <container-name>`

Mount volume for live code reloading?
`docker container run -it --rm --name <container-name> -p <docker-host-port>:<docker-container-port> -e NODE_DEBUG=1 -v $PWD:/opt/app <container-name>`

* Tail logs of running Docker container in real-time:
`docker container logs -f <container-name|ID>`

* Get some real-time metrics about running Docker containers:
`docker container stats`

* Inspect running Docker container:
`docker container inspect <container-name|ID`

* Connect to running Docker container using `sh`:
`docker container exec -it <container-name|ID> sh`

* List running Docker containers:
`docker container ls`

Including stopped ones?
`docker container ls -a`

* Stop running Docker container:
`docker container stop <container-name|ID>`

Multiple containers?
`docker container stop <container-name|ID-1> <container-name|ID-2> …`

In quite mode?
`docker container stop $(docker container ls -a -q)`

* Remove Docker container:
`docker container rm <container-name|ID>`

* How much disk space Docker is using?
`docker system df`

More verbosity?
`docker system df -v`

* Get information about Docker setup (also good to check if Docker is well installed, better than `docker —version`):
`docker system info`

* Remove reclaimable resources:
`docker system prune`

Avoid confirmation?
`docker system prune -f`

Delete all unused Docker images and containers aggressively:
`docker system prune -a`

## Docker Compose
 * Build Docker image(s):
`docker-compose build`

* Pull dependency Docker image(s) if any:
`docker-compose pull`

* Start Docker Compose project:
`docker-compose up`

* Build, pull & start in one command?
`docker-compose —-build`

* List all running Docker containers for Docker Compose project:
`docker-compose ps`

* Tail logs of all running Docker containers associated to Docker Compose project in real-time:
`docker-compose logs -f`

* Connect to running Docker container of specific service using `sh`:
`docker-compose exec <service-name> sh`

* Stop Docker Compose project:
`docker-compose stop`

* Restart Docker Compose project:
`docker-compose restart`

* Remove Docker containers associated to Docker Compose project:
`docker-compose rm`
