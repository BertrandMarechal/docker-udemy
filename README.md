docker-udemy

[Udemy](https://www.udemy.com/docker-mastery/learn/v4/content)

[Git Repo](https://github.com/bretfisher/udemy-docker-mastery)

## docker commands
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
```