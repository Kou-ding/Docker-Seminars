# 1st Seminar Notes
### Preparation
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

### Basic container commands
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

# remove all stopped containers
docker container prune
```

If you want to enter the cli of your container you can do so.
```bash
# i: interactive session
# t: tty environment 
docker run -it --name ubu ubuntu

# after exiting inside of the tty
# a: attach
docker start -ia ubu
# no need to create a tty since it was already created at the run command using the -t flag.
```

It is possible to execute commands on a container even when it is detached(running on the background)
```bash 
# Run a simple nginx container
docker run -d --rm --name web -p 8080:80 nginx:alpine

# While it being detached execute a simple list command inside the container
docker exec web ls -l /usr/share/nginx/html

# Optional: Execute commands (e.g. id) as a certain user of a certain group (here user=1000 group=1000) 
docker exec -u 1000:1000 web id
```


