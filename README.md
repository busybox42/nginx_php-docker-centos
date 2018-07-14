[![](https://images.microbadger.com/badges/image/busybox42/nginx_php-docker-centos.svg)](https://microbadger.com/images/busybox42/nginx_php-docker-centos "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/busybox42/nginx_php-docker-centos.svg)](https://microbadger.com/images/busybox42/nginx_php-docker-centos "Get your own version badge on microbadger.com")
# nginx_php-docker-centos
This repository contains a docker image of CentOS 7 with Nginx, php-fpm and certbot-nginx for ssl if needed.

## Downloading the image
The first step is to pull the image.
```bash
docker pull busybox42/nginx_php-docker-centos
```

## Creating the container
Now that we have the image busybox42/nginx_php-docker-centos we can create the container with a few parameters.

Name the container, expose ports 80 and 443 for a webserver and set a hostname.
```bash
docker run --name nginx -p 80:80 -p 443:443 -h web.myhost.tld busybox42/nginx_php-docker-centos
```
Here is an example of storing the nginx and html configuration on the docker host.
```bash
docker run --name nginx -p 80:80 -p 443:443 -h web.myhost.tld -v /srv/web/nginx:/etc/nginx -v /srv/web/http:/srv/http busybox42/nginx_php-docker-centos
```

## Configuring your server
Nginx configuartion files are located in /etc/nginx.
Store you web files in /srv/http.

Use certbot to create an ssl certificate for your site.
```bash
certbot --nginx -d myhost.tld -d www.myhost.tld
```
