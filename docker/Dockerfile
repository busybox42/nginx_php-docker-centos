#################################################################
# Dockerfile to build a nginx/php-fpm container image
# Based on CentOS 7
# Created by Alan Denniston
#################################################################
FROM centos:latest
MAINTAINER Alan Denniston <alan.denniston@gmail.com>

RUN yum update -y --nogpgcheck &&  yum install -y epel-release && yum install -y --nogpgcheck \
  nginx \
  php \
  php-mysql \
  php-ldap \
  php-fpm \
  certbot-nginx \
  && yum clean all \
  && yum clean metadata

VOLUME ["/srv/http"]

EXPOSE 80/tcp 443/tcp

ENTRYPOINT /usr/sbin/php-fpm --daemonize && /usr/sbin/nginx -t && /usr/sbin/nginx && /bin/bash

CMD ["true"]
