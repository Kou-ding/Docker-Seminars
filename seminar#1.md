# 1st Seminar Notes
### Basics
Quality of life docker tip
```bash
# add user to docker group to avoid using sudo all the time
# restart for the changes to take effect
sudo usermod -aG docker $USER
```

Getting started
```bash
# print docker version
docker --version
# print docker info
docker info
```

My first container
```bash
# run: run a container
# -d: detached mode (runs container in the background *bg process*)
# --rm: automatically removes the container when it stops
# --name: container's name e.g. nginx-web
# -p: <hostport>:<containerport> where *hostport* is the localhost port on your pc the container will run on and *containerport* is the predetermined port containers run on (specific for each container e.g. nginx runs on container port 80)
# nginx:alpine: <>:<>
docker run -d --rm --name nginx-web -p 8080:80 nginx:alpine
```

Containers are active instances of a docker image and docker images can become containers when run.
```bash
# see all your docker images
docker image ls

# see all your docker containers
docker ps

# stop a container
docker stop nginx-web

# if you dont use the --rm option when running a container it will remain and can be seen using the following -a option
docker ps -a

# to completelly remove it use
docker rm nginx-web

# remove an image
docker rmi nginx:alpine
```

Advanced commands
```bash
# remove all stopped containers
docker container prune
```


