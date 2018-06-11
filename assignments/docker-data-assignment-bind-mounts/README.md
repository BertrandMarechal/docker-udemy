# run a webserver and see the updates doen on the files

Lecture 47

- [ ] start container using "docker container run -p 80:4000 -v $(pwd):/site bretfisher/jekyll-serve"
- [ ] go in the post directory and do some changes
- [ ] refresh the page, and see the changes

use a jekyll "static Site generator" to start a local web server

```bat
# start the container
# docker container run -d -p 80:4000 -v ${pwd}:/site --name jekyll bretfisher/jekyll-serve
docker container run -d -p 80:4000 -v c:/Users/Bertrand.Marechal/Documents/Projects/GitHubBertrand/docker-udemy/assignments/docker-data-assignment-bind-mounts:/site --name jekyll bretfisher/jekyll-serve
# small c and proper path / separated
```