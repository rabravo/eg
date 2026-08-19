# docker

pull an image from Docker Hub

    docker pull ubuntu:22.04


pull an image for a specific platform (e.g. amd64 on Apple Silicon)

    docker pull --platform linux/amd64 drabravo/ou-csi3450-container:latest

    # --platform linux/amd64   force amd64 image even on ARM Macs (Apple Silicon)
    # drabravo/ou-csi3450-...  image on Docker Hub: <user>/<repo>:<tag>
    # :latest                  tag — use a version tag (e.g. :1.0) for reproducibility


stop a running container and remove it so the name can be reused

    docker stop csi3450_phpmyadmin && docker rm csi3450_phpmyadmin

    # docker stop   sends SIGTERM, waits for graceful shutdown
    # docker rm     deletes the stopped container (frees the name and writable layer)
    # &&            only runs rm if stop succeeds


start a fresh container from the course image

    docker run --platform linux/amd64 -d --name csi3450_phpmyadmin \
               -p 8888:8888 -p 80:80 \
               drabravo/ou-csi3450-container:latest

    # --platform linux/amd64        run the amd64 image (matches what was pulled)
    # -d                            detached — runs in the background, returns the container ID
    # --name csi3450_phpmyadmin     assign a memorable name instead of a random one
    # -p 8888:8888                  map host port 8888 → container port 8888 (app/Jupyter)
    # -p 80:80                      map host port 80 → container port 80 (phpMyAdmin / web)


run a container interactively and remove it on exit

    docker run -it --rm ubuntu:22.04 bash


run a container in the background (detached)

    docker run -d --name myapp nginx


run with a port mapping (host:container)

    docker run -d -p 8080:80 nginx


run with a volume mount

    docker run -d -v /host/path:/container/path nginx


run with an environment variable

    docker run -e DATABASE_URL=postgres://... myapp


run a one-off command in a new container

    docker run --rm python:3.11 python -c "print('hello')"


open a shell in a running container

    docker exec -it myapp bash


open a shell in the course container

    docker exec -it csi3450_phpmyadmin bash

    # docker exec              run a command inside an already-running container
    # -i                       keep stdin open (needed for interactive input)
    # -t                       allocate a pseudo-TTY (gives you a proper terminal prompt)
    # csi3450_phpmyadmin       target container, identified by its --name
    # bash                     command to run — opens a Bash shell inside the container


run a command in a running container

    docker exec myapp cat /etc/hosts



# Images

list local images

    docker images

    # docker images    list all images stored locally
    # columns:         REPOSITORY  — image name (e.g. drabravo/ou-csi3450-container-amd64)
    #                  TAG         — version label (e.g. latest)
    #                  IMAGE ID    — short content hash, unique identifier for the image
    #                  SIZE        — uncompressed size on disk


build an image from a Dockerfile in the current directory

    docker build -t myapp:latest .


build with a build argument

    docker build --build-arg ENV=production -t myapp .


tag an image

    docker tag myapp:latest registry.example.com/myapp:1.0


push an image to a registry

    docker push registry.example.com/myapp:1.0


remove an image

    docker rmi myapp:latest


remove all dangling (untagged) images

    docker image prune


remove all unused images

    docker image prune -a



# Containers

list available (all) containers

    docker ps -a

    # docker ps     list containers (default: running only)
    # -a            show all — running, stopped, and exited


list only running containers

    docker ps


stop a container gracefully

    docker stop myapp


kill a container immediately

    docker kill myapp


start a stopped container

    docker start myapp


restart a container

    docker restart myapp


remove a stopped container

    docker rm myapp


stop and remove a container in one step

    docker rm -f myapp


view container logs

    docker logs myapp


view logs for the course container

    docker logs csi3450_phpmyadmin

    # docker logs              print stdout/stderr captured from the container
    # csi3450_phpmyadmin       the container name assigned with --name at run time


stream logs in real time

    docker logs -f myapp


show the last 50 log lines

    docker logs --tail 50 myapp


inspect container metadata (IP, mounts, env vars, etc.)

    docker inspect myapp


inspect the course container

    docker inspect csi3450_phpmyadmin

    # docker inspect           output full container metadata as JSON
    # csi3450_phpmyadmin       target container, identified by its --name
    # useful fields:           .NetworkSettings.IPAddress  — container's internal IP
    #                          .Mounts                     — volume and bind mount details
    #                          .Config.Env                 — environment variables
    #                          .State                      — running, exit code, started/finished times


show resource usage (CPU, memory) of running containers

    docker stats



# Volumes and Networks

list volumes

    docker volume ls


create a named volume

    docker volume create mydata


mount a named volume into a container

    docker run -d -v mydata:/data myapp


remove a volume

    docker volume rm mydata


prune unused volumes

    docker volume prune


list networks

    docker network ls


create a bridge network

    docker network create mynet


connect a container to a network

    docker network connect mynet myapp


run a container on a specific network

    docker run -d --network mynet myapp



# Docker Compose

start all services defined in docker-compose.yml

    docker compose up


start in the background

    docker compose up -d


stop all services

    docker compose down


stop and remove volumes

    docker compose down -v


rebuild images before starting

    docker compose up --build


stream logs from all services

    docker compose logs -f


run a one-off command in a service container

    docker compose run --rm web bash


scale a service to 3 replicas

    docker compose up -d --scale worker=3


show status of services

    docker compose ps



# Cleanup

remove all stopped containers, unused networks, dangling images, and build cache

    docker system prune


also remove unused volumes

    docker system prune --volumes


show disk usage by Docker objects

    docker system df


