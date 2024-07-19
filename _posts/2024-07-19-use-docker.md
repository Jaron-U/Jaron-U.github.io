---
title: 'Use Docker to create a Ubuntu 20.04 image'
date: 2024-07-19
permalink: /posts/use-docker/
tags:
  - Opearting System
  - Docker
  - Ubuntu 20.04

---

## Use Docker to create a Ubuntu 20.04 image

### 1. Install Docker

```bash
sudo apt update
# install docker.io
sudo apt install docker.io

# start docker
sudo systemctl start docker
sudo systemctl enable docker

# add user to docker group
sudo usermod -aG docker $USER
newgrp docker # refresh group

# pull ubuntu 20.04 image
docker pull ubuntu:20.04

# create a new container
sudo docker run -it --name ubuntu20_env -v /path/to/your/local/project:/project ubuntu:20.04

# now you are in the ubuntu 20.04 container
```
### 2. Install necessary packages for Ubuntu 20.04

```bash
apt update
apt install sudo -y

# download the necessary install bash script
sudo apt install curl
curl -o src-cloud.zip https://seed.nyc3.cdn.digitaloceanspaces.com/src-cloud.zip

sudo apt update
sudo apt -y install unzip
unzip src-cloud.zip
cd src-cloud/
./install.sh

# Now you can go to the ~/project directory and start your project

```

### 3. Exit and start the container
```bash
# exit the container
exit

# start the container
docker start -ai ubuntu20_env

# remove the container
docker rm ubuntu20_env
```

### 4. Save and load the container
```bash
# save the container
docker save -o ubuntu20.tar ubuntu:20.04

# load the container in another machine
docker load -i ubuntu20.tar
```