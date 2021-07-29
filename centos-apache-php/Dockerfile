FROM webdevops/php-apache-dev:centos-7
LABEL maintainer="vo son"
LABEL version="1.0"

RUN yum -y update

# install httpd 2.4
RUN yum -y install httpd

RUN yum -y install gmp-devel mpfr-devel libmpc-devel wget gcc

# git + curl
RUN yum install -y git curl zip

RUN yum install epel-release -y
RUN yum install -y http://rpms.remirepo.net/enterprise/remi-release-7.rpm
RUN yum -y install yum-utils

# install php 7.4
RUN yum-config-manager --enable remi-php74 \
    && yum update -y \
    && yum --enablerepo=remi-php74 install php -y

RUN yum -y install php php-fpm php-mcrypt php-cli php-common php-devel php-gd php-mbstring php-mysqlnd php-opcache php-pdo php-pear php-pecl-apcu php-pecl-zip php-intl php-process php-xml php-pecl-xdebug php-xdebug git php-ldap php-pecl-memcached php-pgsql php-pecl-redis php-pecl-memcache php-gd  php-zib

RUN yum -y install policycoreutils-python

# install imagick
RUN yum -y install php-pecl-imagick

# install node js
# nodejs 12 LTS
RUN yum install -y gcc-c++ make \
    && curl -sL https://rpm.nodesource.com/setup_14.x | bash - \
    && yum -y install nodejs

# composer
RUN cd /tmp \
    && curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# RUN docker-service enable syslog \
#     && docker-service enable postfix \
#     && docker-service enable ssh \
#     && docker-run-bootstrap \
#     && docker-image-cleanup \
