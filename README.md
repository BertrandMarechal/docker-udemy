# docker-udemy

[Udemy](https://www.udemy.com/docker-mastery/learn/v4/content)

[Git Repo](https://github.com/bretfisher/udemy-docker-mastery)

## docker commands for lecture 2-18 - first steps
```bat
# 1 run a webserver container
docker container run --publish 80:80 nginx

# 2 list the running containers
docker container ls

# 3 list all the containers
docker container ls -a

# 4 stop a container
docker container stop [CONTAINER ID from 2]

# 5 run a webserver container with a name
docker container run --publish 80:80 --name webhost nginx

# 6 get the docker logs
docker container logs [webhost]

# 7 display the running processes ot a container
docker container top [webhost]

# 8 remove multiple containers
# the command can accept multiple ids
docker container rm [ID 1] [ID 2]

# 9 remove containers forcing stop
# the command can accept multiple ids
docker container rm -f [ID 1]

# BONUS 10 remove all processes
docker rm $(docker ps -a -q)
```

## docker commands for lecture 2-19 - just a process
```bat

# 1 start a mongo db container
docker container run --name mongo -d mongo

# 2 get the running processes
docker container top mongo
```

## Homewrok : lecture 2-21
Tasks :
- [x] Create 3 dockers : nginx, mysql and httpd (apache server)
- [x] Detach them
- [x] Give them a name
- [x] Give them ports (80 for nginx, 8080 for httpd, 3306 for mysql)
- [x] For MySQL, use the option MYSQL_RQNDOM_ROOT_PQSSWORD=yes with the --env option
- [x] Stop them all
- [x] Remove them all

### my code for that
```bat
# 1. create nginx container
docker container run --publish 80:80 --detach --name nginx nginx

# 2. create  mysql container
docker container run --publish 3306:3306 --detach --name mysql --env MYSQL_RANDOM_ROOT_PASSWORD=yes mysql

# 3. create  httpd container
docker container run --publish 8080:80 --detach --name httpd httpd

# 4. list the containers
docker container ls

# 5. stop the containers
docker container stop [CONTAINER IDS]

# 6. remove the containers
docker container rm [CONTAINER IDS]
```

## monitor dockers : lecture 2-23
```bat
# 1. For stats on all containers
docker container stats

# 2. For info on container
docker container info [name]
```

## interract with containers : lecture 2-24
```bat
# 1. Run a container in interractive mode, with a bash CLI
docker container run -it --name proxy nginx bash

# 2. Run a container in interractive mode, with a bash CLI - ubuntu mode
docker container run -it --name ubuntu ubuntu

# 3. Run a container already defined with interracted mode
docker container start -ai ubuntu

# 4. Interract with a running container with interracted mode
docker container exec -it mysql bash

# 5. list docker images
docker image ls

# 6. create an alpine container (sh is the smallest equivalent to bash)
docker container run -it alpine bsh
```

## Docker networks : lecture 2-25
```bat
# 1. Run a container on port 80:80
docker container run -p 80:80 -d --name webhost nginx

# 2. Get the docker container port definition
docker container port webhost

# 3. Format the reruned data -- IP address of the container
docker container inspect --format '{{ .NetworkSettings.IPAddress}}' webhost
```

## Docker networks - CLI : lecture 2-27
```bat
# 1. List docker networks
docker network ls

# 2. inspect docker network
docker network inspect [network name]

# 3. create a new docker network
docker network create [network name]

# 4. create a container on the created network
docker container run -d --name new_nginx --network my_app_network nginx

# 5. connect a container to an existing network
docker network connect [my_app_net] [nginx]

# 6. the inspect command on the container will show us the networks
docker container inspect [nginx]

# 7. connect a container to an existing network
docker network disconnect [my_app_net] [nginx]
```

## Docker networks - DNS : lecture 2-28
```bat
# 1. Create a new container with the nginx:alpine implementation
docker container run --name my_nginx -d --network my_app_net nginx:alpine

# 2. Ping between containers that are on the same network
docker container exec -it my_nginx ping new_nginx
```

## Docker networks - DNS : lecture 2-29
Homework : run the curl command inside 2 linux distributions
- [ ] create a container on centos:7 -it bash
- [ ] create a container on ubuntu:14.04 -it bash
- [ ] learn about "docker container --rm" command
- [ ] check if curl is installed
- [ ] install it if needed ("apt-get update" and "apt-get install curl", or "yum update curl")
