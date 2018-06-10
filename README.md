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