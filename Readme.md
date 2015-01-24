## Nginx Dockerfile

This repository is cloned from  **Dockerfile** of [Nginx](http://nginx.org/) for [Docker](https://www.docker.com/)'s [automated build](https://registry.hub.docker.com/u/dockerfile/nginx/) published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [dockerfile/ubuntu](http://dockerfile.github.io/#/ubuntu)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/dockerfile/nginx/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull dockerfile/nginx`

   (alternatively, you can build an image from Dockerfile: `docker build -t="wheretolive/nginx_dtk" ./dockers/nginx`)


### Usage

    docker run -d -p 80:80 dockerfile/nginx

#### Attach persistent/shared directories

    docker run -d -p 80:80 -v <sites-enabled-dir>:/etc/nginx/sites-enabled -v <certs-dir>:/etc/nginx/certs -v <log-dir>:/var/log/nginx -v <html-dir>:/var/www/html dockerfile/nginx

After few seconds, open `http://<host>` to see the welcome page.

### DTK configuration to run

starting from the datatoknowledge.it folder

	1. docker run -d --name dtk2 -e VIRTUAL_HOST=datatoknowledge.it -v "$(pwd)"/dockers/nginx/sites-enabled:/etc/nginx/sites-enabled -v "$(pwd)"/dockers/nginx/log:/var/log/nginx -v "$(pwd)":/var/www/ wheretolive/nginx_dtk

    2. docker run -d -p 80:80 -v "$(pwd)"/dockers/nginx/sites-enabled:/etc/nginx/sites-enabled -v "$(pwd)"/dockers/nginx/log:/var/log/nginx -v "$(pwd)":/var/www/ wheretolive/nginx_dtk

the configuration 1 should be used after reading [this link](http://jasonwilder.com/blog/2014/03/25/automated-nginx-reverse-proxy-for-docker/).
The configuration 2 is deprecated