# Docs
* [Docker Docs](https://docs.docker.com/)
* [Dockerfile reference](https://docs.docker.com/reference/dockerfile/)
 
# [Install](https://docs.docker.com/engine/install/ubuntu/)
   1. `sudo apt update`
   1. `sudo apt install ca-certificates`
   1. Add Docker's official GPG key:
      1. Set permissions to the `/etc/apt/keyrings` directory: `sudo install -m 0755 -d /etc/apt/keyrings`
      1. Load the Docker GPG key: `sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc`
      1. Update the loaded key permissions: `sudo chmod a+r /etc/apt/keyrings/docker.asc`
   1. Add Docker repository to the `apt` sources:
   ```
   echo \
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
     $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
     sudo tee /etc/apt/sources.list.d/docker.list > /dev/null     
   ```
   1. `sudo apt update`
   1. Install the latest Docker version: `sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`
   1. Verify the installation: `sudo docker run hello-world`

# CLI

## Images
* Download an image from Docker registry: `sudo docker pull <IMAGE_NAME>`
* Check the downloaded images: `sudo docker images`
* Build an image: `docker build <IMAGE_NAME>`
* Run an image: `docker run <IMAGE_NAME>`
* Remove an image: `docker rmi IMAGE <REPOSITORY:TAG>`
* Forcefully Remove all images: `docker rmi -f $(docker images -q)`

## Containers
* Statistics for running containers: `sudo docker stats`
* List of all containers: `sudo docker ps -a`
* List container mounts: `docker inspect -f '{{ .Mounts }}' <container id>`
* Start a container: `docker start <CONTAINER_ID>`
* Container info: `docker inspect <CONTAINER_ID>`
  * Container status: `docker inspect --format='{{.State.Status}}' <CONTAINER_ID>`
  * Container mappings: `docker inspect -f '{{ .Mounts }}' <CONTAINER_ID>`
* List of processes in a container: `docker top <CONTAINER_ID>`
* Container logs: `docker logs <CONTAINER_ID> | less`
  * `sudo docker logs <CONTAINDER_ID> -n 100 -f --timestamps`
* Restart container: `sudo docker restart <CONTAINER_ID>`
* Access container: `sudo docker exec -ti <CONTAINER_ID> /bin/bash`
* Stop container: `sudo docker stop <CONTAINER_ID>`
* Stop all running containers: `docker stop $(docker ps -aq)`
* Remove a container: `sudo docker rm <CONTAINER_ID>` 
* Remove all containers: `docker container rm $(docker container ls -aq)`

## Services
* List of services: `docker-compose ps`
* Start a service: `docker-compose start <SERVICE_NAME>` Or `docker-compose up -d <SERVICE_NAME>`
  * in foreground: `docker-compose up <SERVICE_NAME>`
* Service logs: `docker-compose logs <SERVICE_NAME>`
* Access a service: `docker-compose exec <SERVICE_NAME> bash`
* Stop a service: `docker-compose stop <SERVICE_NAME>`
* Remove a service: ` docker-compose rm <SERVICE_NAME>`

## Networks
* List of networks: `docker network ls`
* Network info: `docker network inspect cpp_dev`

## Util
* Remove all orphan containers, images w/o containers, unused networks etc: `docker system prune -a`
* Copy into container: `docker cp <FILE> <CONTAINER_ID>:/<DESTINATION>/`
* Copy from container: `docker cp <CONTAINER_ID>:/<FILE> /<DESTINATION>/`
