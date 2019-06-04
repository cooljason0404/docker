# This create php
# Version 1
# Author: Jason

# CentOS
FROM centos:7
MAINTAINER Jason

ENV PHP_VERSION=7.2.13

RUN yum -y install epel-release
RUN yum -y install libxml2-devel openssl-devel libcurl-devel gd gd-devel libmcrypt libmcrypt-devel libtool
RUN yum -y install gcc automake autoconf libtool make
RUN yum -y update 
RUN groupadd www
RUN useradd -g www www

RUN mkdir -p /var/install/

# libzip-1.2.0
#ADD libzip-1.2.0.tar.gz /var/install/
#WORKDIR /var/install/libzip-1.2.0
#RUN ./configure
#RUN make && make install
#RUN cp /usr/local/lib/libzip/include/zipconf.h /usr/local/include/zipconf.h

# install php 
ADD php-${PHP_VERSION}.tar.gz /var/install/
WORKDIR /var/install/php-${PHP_VERSION}
RUN	./configure --prefix=/usr/local/php-${PHP_VERSION} \
    --with-fpm-user=www -with-fpm-group=www \
    --enable-fpm --enable-mysqlnd --with-pdo-mysql=mysqlnd --with-mysqli=mysqlnd \
    --with-zlib --with-iconv --with-mhash --with-gd --with-openssl --with-freetype-dir --with-curl \
    --with-png-dir --with-jpeg-dir --with-libxml-dir --with-gettext --enable-mbstring --enable-zip \
    --enable-sockets --enable-soap --enable-bcmath --enable-ftp --enable-pcntl --enable-opcache --enable-xml --enable-phar
RUN make && make install

RUN ln -sf /usr/local/php-${PHP_VERSION}/ /usr/local/php
RUN cp /var/install/php-${PHP_VERSION}/php.ini-production /usr/local/php/lib/php.ini
RUN cp /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf
ADD /config/www.conf /usr/local/php/etc/php-fpm.d/
ENV PATH /usr/local/php/bin:/usr/local/php/sbin:$PATH

WORKDIR /
CMD ["php-fpm", "-F"]