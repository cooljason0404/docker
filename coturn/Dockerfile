# This create coturn server
# Version 1
# Author: Jason <cooljason0404@gmail.com>

# CentOS
FROM centos:7
MAINTAINER Jason

RUN yum install -y make gcc cc gcc-c++
RUN yum install -y openssl-devel libevent2 libevent-devel 
RUN yum install -y sqlite sqlite-devel postgresql-devel postgresql-server mysql-devel mysql-server hiredis hiredis-devel

#https://github.com/coturn/coturn/archive/4.5.1.1.tar.gz

ADD 4.5.1.1.tar.gz /var/install/