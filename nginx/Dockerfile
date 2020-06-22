FROM ubuntu:14.04
LABEL maintaner="Meshari Alnaim <malnaim@safedecision.com.sa>"
LABEL name="dev"
LABEL version="v1"
ADD hello.html /usr/share/nginx/html
RUN apt-get update && apt-get -y upgrade 
RUN apt install -y nginx
