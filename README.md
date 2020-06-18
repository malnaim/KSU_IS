# Docker "FROM scratch"
```
Title : Docker "FROM scratch"
Author : Meshari Alnaim <malnaim@safedecision.com.sa>
Date : 
KSU IS 

```
## Course Introduction
  * What is Docker ?
## Installation and Configuration: 
  * Linux (Ubuntu, Debian, CentOS, Fedora, Raspbian ... etc) <https://docs.docker.com/engine/install/> 
  * MacOS got to <https://hub.docker.com/editions/community/docker-ce-desktop-mac/>
  * Windows go to <https://hub.docker.com/editions/community/docker-ce-desktop-windows/>
 
## Docker Hub Basics
  * <https://hub.docker.com/>
## Docker Images
  * Standardize our development environment (i.e. ubuntu LTS 16.04 using python 2.7 ) from development to production.
  * Secure our environment . 
```bash
docker pull ubuntu:16.04
```
 The Dockerfile
  * Create a file named Dockerfile and add the following docker commands
``` dockerfile
FROM ubuntu:16.04
LABEL maintaner="Meshari Alnaim <malnaim@safedecision.com.sa>"
LABEL name="dev"
LABEL version="v1"
RUN apt-get update && apt-get -y upgrade 
RUN apt install -y python
```
  * Save the Dockerfile and run the following command to build the Dockerfile in the corrent directory 
``` bash
docker build .
```
  * Check the images 
```
# Legacy command
docker images 
# updated command
docker image ls
```
## Running Containers
* list all the images
``` bash
dokcer image ls
``` 
* Now lets run the container 
``` bash
# we run ubuntu 16.04 docker container name is_dev
docker run -it --name is_dev ubuntu:16.04
```
* install python and nano in the container
``` bash
apt update
apt install -y nano python
nano hello.py
# add the two lines in to the python script
#!/usr/bin/env python
print("Hello IS Students !")
# now exit and make the script executable
chmod +x hello.py
python hello.py
```

## The Container Lifecycle

``` bash
docker images
docker container ls
docker container ls -a
docker container start is_dev
docker attach is_dev
```
## Container and Image Management
```
docker container ls -a
docker images 
docker container rm is_dev
docker rmi <image_name>
docker push 
```
## Redirection: Docker Container Ports
## Redirection: Docker Container Volumes
## Choose Your Own Adventure: Where Do I Go from Here?
## Hands-On Lab:
## Working with Docker Images
## Course Incomplete
