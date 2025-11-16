# 2nd Seminar Notes

### Volumes
In order to keep data in containers we create volumes
```bash
# create a volume
docker volume create site

# inspect where the volume is mounted
docker volume inspect site

## Edit volume using a light busybox container
# Busybox is a stripped down implementation of many UNIX commands
# -v: volume flag <volume_name>:<path_inside_busybox_container> 
docker run --rm -it -v site:/site busybox sh -c 'echo "<h1>GreekLUG Docker Volumes</h1>" > /site/index.html'

## Run a nginx container having mounted the site volume 
# type: <volume>
# source: <volume_to_mount>
# target: <directory_to_mount_volume>
# ,ro: read only
docker run -d --name web -p 8080:80 --mount type=volume,source=site,target=/usr/share/nginx/html,ro nginx:alpine
```

### Networks
In order for the containers to talk to each other we create a network.
```bash
# list all networks
docker network ls

# create a network
docker network create <name>

# inspect a network's details
docker network inspect <name>

# connect a container to a network
docker network connect <network_name> <container_name>

```