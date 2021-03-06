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
apt install -y nano python nginx
# Nginx example
nano nano /var/www/html/index.nginx-debian.html
service nginx start
nginx -s reload
service nginx reload
# Python example 
nano hello.py
# add the two lines in to the python script
#####
#!/usr/bin/env python
print("Hello IS Students !")
#####
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
``` bash
docker container ls -a
docker images 
docker push malnaim/ksu_is:v1
docker container rm is_dev
docker rmi <image_name>
```
## Docker Container Ports
``` bash
docker run -itp 8080:80 --name is_dev ubuntu:16.04
``` 
## Docker Container Volumes
``` bash 
docker run -itp 8080:80 --volume /home/USER/Code/KSU_IS/html:/var/www/html:ro --name is_dev ubuntu:16.04
```
## **UPDATE Nodejs Docker app Example**
* First let's create our first Javascript file called "server.js" and write the following javascript code :
``` javascript
var http = require('http');

function onRequest(request, response) {
    response.writeHead(200, {'Content-Type': 'text/plain'});
    response.write('Hello KSU Students');
    response.end();
}

http.createServer(onRequest).listen(8000); 
```
* Create our Dockerfile and *COPY* our code into the Dockerfile
``` Dockerfile
FROM node
WORKDIR /app   # change to app directory 
COPY server.js .
USER node
EXPOSE 8000
CMD ["node", "server.js"]
```
* Build the image 
```bash
docker build -t js:latest .
```
* Run the container 
``` bash
docker run -itp 8080:8000 --name js_server js
```
----
# Resources 
### Docker remove commands
``` bash
docker stop (docker ps -a -q)
docker rm (docker ps -aq)
docker rmi (docker images -aq)
```
* <https://labs.play-with-docker.com/>
* <https://code.visualstudio.com/docs/containers/quickstart-node>
* <https://www.docker.com/101-tutorial>
* <https://github.com/IBMStockTrader/portfolio>
* <https://hub.docker.com/r/ibmstocktrader/portfolio>
* <https://cloud.linode.com>
* <https://github.com/malnaim/KSU_IS>