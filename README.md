# Docker Commands Cheat Sheet

Project is about Docker commands

##### GENERAL
```
Login to your docker account
  $ docker login --username=<username>  // This will prompt you password

Check all the running docker instances
  $ docker-machine ls

Check installed docker version
  $ docker version

Check installed images
  $ docker images
  
All running contains
(Wildcard: -a - To include previously running containers in list)
  $ docker ps

Check detailed information of provided docker
  $ docker inspect <container_ID>
  
Check image layers (Layers are nothing but images within docker image)
  $ docker history <container_name>:<tagname>

Check Network modal of docker
  $ docker network ls
```
##### CONTAINER COMMANDS
```
This will install latest version of busybox image and show "Hello worlds" after completion (Syntax: docker run repository:tag command [arguments])
  $ docker run busybox:latest echo "Hello world"

To run particular container
Wildcards:
-i: Interactive mode
-t: Allocate a pseudo-TTY
-d: In Detached mode (In background)
--name container_name (This will allocate name to container, instead random name provided by docker)
  $ docker run -i -t busybox:latest

Save changes to your own container by creating new container
  $ docker commit <container_ID> <repository_name:tag>

To build new container (-t tag new image, --no-cache can be used to run the entire commands without cache)
  $ docker build -t gsin11/debian:1.1 --no-cache=true

COMMAND inside docker image
  $ docker exec -it <container_ID> <command>
  $ docker exec -it 534g1ba6j bash
```
##### Dockerfile COMMANDS
```
COPY COMMAND (You can write this command into your Dockerfile)
  $ COPY <source_filepath> <destination_filepath>

ADD COMMAND (Similar to COPY, but it can download file and then upload it to docker image. It also works with zip file and then unzip it inside the docker)
  $ COPY <source_filepath.zip/remote_path> <destination_filepath>
```
##### DOCKER COMPOSE
```
To run multiple docker images together

Run docker container (Add -d to run on background)
  $ docker-compose up
  
Stop docker container
  $ docker-compose stop // Note: It will stop all the containers
  $ docker-compose stop <container_ID>
  
Remove container
  $ docker-compose rm <container_ID>

Update image, it will be helpful when you want to make any changes inside the container
  $ docker-compose build
  
Logs
  $ docker-compose logs // Tip: -f for tailing logs
```
##### REAL WORLD EXAMPLES
```
Run container in closed/None network model (Note: You won't get internet access inside this container)
  $ docker run -d --net none busybox sleep 1000

Create new network with my_bridge_network (drive name can be: bridge/overlay)
  $ docker network create --driver bridge my_bridge_network

Connect container to network
  $ docker network connect my_bridge_network container_3

Create new container with host network model (Note: This networks comes with minimal level of security)
  $ docker run -d --name container_4 --net host busybox sleep 1000

Run command from dockerapp (dockerapp is container name followed by the command)
  $ docker-compose run dockerapp python test.py
```
##### DOCKER MACHINE
```
Installed docker machines
  $ docker-machine ls

Create new docker machine
  $ docker-machine create --driver virtualbox docker-app-machine-name  // list of available drivers: https://docs.docker.com/machine/drivers/
```

#### Feel free to Glow
