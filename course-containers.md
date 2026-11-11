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


## madangel (PDF / image research viewer)

pull the madangel image

    docker pull drabravo/madangel-container:latest

### User — web interface

open the viewer in a browser

    http://localhost:8080

sign in with your username and password, then use the **Projects** group in the left panel:

| Action | How |
|---|---|
| Build a new collection | Click **New Project** → drop a file → pick pages → set title → **Build project** |
| Add pages to a collection | Click **Add Pages to Project** → drop a file → pick pages → **Add pages to project** |
| Rename a collection | Click **Rename Project** |
| Backup a collection | Click **↓ Backup Project** → saves a `.madangel` encrypted file |
| Restore a collection | Click **↑ Import Project** → drop a `.madangel` file |

accepted file formats: **PDF**, **PNG**, **JPG/JPEG**, **TIF/TIFF**
(TIFF files from microscopes: acquisition metadata is extracted automatically into the Notes tab)

AI transcription runs automatically when `ANTHROPIC_API_KEY` is set in the environment;
without it every page falls back to OCR text.

### Admin — container management

start the container (recommended: use compose so env vars and volume are set correctly)

    cd ~/Desktop/oaklandmi/03_research/mad-angel
    MONGODB_URI=mongodb://host.docker.internal:27017 \
    ANTHROPIC_API_KEY=sk-ant-...  \
    docker compose up -d

    # MONGODB_URI       required for login/auth — points to the host MongoDB instance
    # ANTHROPIC_API_KEY optional — enables AI transcription; omit to use OCR only

    # the named volume created by compose is:  madangel-data
    # data directory inside the container:     /data

build a project from a file via the CLI (admin/shell path)

    docker exec madangel madangel new book.pdf --title "My Book" --lang eng

    # --lang spa  or  eng+spa  for Spanish
    # --pages 36,43  for a trial run on two pages
    # accepted: .pdf  .png  .jpg  .jpeg  .tif  .tiff

stop and remove the container (project data stays in the volume)

    docker stop madangel && docker rm madangel

remove the project volume (irreversible — back up first from Project › Backup)

    docker volume rm madangel-data
