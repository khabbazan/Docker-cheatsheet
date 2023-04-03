# Docker cheat sheet

Hi! I'm your first Markdown file in **StackEdit**. If you want to learn about StackEdit, you can read me. If you want to play with Markdown, you can edit me. Once you have finished with me, you can create new files by opening the **file explorer** on the left corner of the navigation bar.


## Create container and execute with bash

```bash
docker create -it --name new-container <image>
docker start new-container
docker exec -it new-container bash
```

## Share a directory to container and execute it

```bash
docker create -it --name new-container -v ~/configs:/home/configs <image>
docker start new-container
docker exec -it new-container bash
```

## Change container and commit in to new image

```bash
docker run -it ubunut bin/bash
```
inside container do something and exit:
```bash
apt-get install nmap
nmap --version
exit
```
get container id:
```bash
docker ps -a
```
commit changes to new image:
```bash
docker commit [CONTAINER_ID] [new_image_name]
```

## Tag an image and push to local registry
tag an image:
```bash
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
docker tag ubuntu:latest ubuntu:myubuntu
```
push to local registry:
```bash
docker tag <source-image-name>:<source-tag-name> localhost:5000/<newimage>
docker push localhost:5000/<newimage>:<tag-name>
```
