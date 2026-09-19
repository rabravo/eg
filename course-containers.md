# course containers


## CSI 1210

pull the CSI 1210 course image

    docker pull --platform linux/amd64 drabravo/ou-csi1210-container:latest

start a fresh container from the CSI 1210 course image

    docker run -d \
    --platform linux/amd64 \
    --name csi1210_ca \
    -p 8888:8888 \
    -v ~/Desktop/csi1210:/home/csi1210/work \
    drabravo/ou-csi1210-container:latest

    # -d                          detached — runs in the background
    # --name csi1210_ca           assign a memorable name
    # -p 8888:8888                host port 8888 → container port 8888 (Jupyter)
    # -v ~/Desktop/csi1210:...    bind-mount local work folder into the container

stop and remove the CSI 1210 container

    docker stop csi1210_ca && docker rm csi1210_ca


## CSI 1320

pull the CSI 1320 course image

    docker pull --platform linux/amd64 drabravo/ou-csi1320-container:latest

start a fresh container from the CSI 1320 course image

    docker run -d \
    --platform linux/amd64 \
    --name csi1320_lab \
    -p 8888:8888 \
    -v ~/Desktop/csi1320:/home/csi1320/work \
    drabravo/ou-csi1320-container:latest

    # -d                          detached — runs in the background
    # --name csi1320_lab          assign a memorable name
    # -p 8888:8888                host port 8888 → container port 8888 (Jupyter)
    # -v ~/Desktop/csi1320:...    bind-mount local work folder into the container

stop and remove the CSI 1320 container

    docker stop csi1320_lab && docker rm csi1320_lab


## CSI 3210

pull the CSI 3210 course image

    docker pull --platform linux/amd64 drabravo/ou-csi3210-container:latest

start a fresh container from the CSI 3210 course image

    docker run -d \
    --platform linux/amd64 \
    --name csi3210_ca \
    -p 8888:8888 -p 5001:5000 \
    -v ~/Desktop/csi3210:/home/csi3210/work \
    drabravo/ou-csi3210-container:latest

    # -d                          detached — runs in the background
    # --name csi3210_ca           assign a memorable name
    # -p 8888:8888                host port 8888 → container port 8888 (Jupyter)
    # -p 5001:5000                host port 5001 → container port 5000 (app server)
    # -v ~/Desktop/csi3210:...    bind-mount local work folder into the container

stop and remove the CSI 3210 container

    docker stop csi3210_ca && docker rm csi3210_ca


## CSI 3450

pull the CSI 3450 course image

    docker pull --platform linux/amd64 drabravo/ou-csi3450-container:latest

start a fresh container from the CSI 3450 course image

    docker run -d \
    --platform linux/amd64 \
    --name csi3450_phpmyadmin \
    -p 8888:8888 -p 80:80 \
    drabravo/ou-csi3450-container:latest

    # -d                          detached — runs in the background
    # --name csi3450_phpmyadmin   assign a memorable name
    # -p 8888:8888                host port 8888 → container port 8888 (Jupyter)
    # -p 80:80                    host port 80 → container port 80 (phpMyAdmin / web)

stop and remove the CSI 3450 container

    docker stop csi3450_phpmyadmin && docker rm csi3450_phpmyadmin
