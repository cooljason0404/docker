# This create mysql
# Version 1
# Author: Jason <cooljason0404@gmail.com>

# CentOS
FROM centos:7
MAINTAINER Jason

ENV MYSQL_VERSION=5.7.25
RUN groupadd mysql
RUN useradd mysql -g mysql -s /bin/false

RUN yum -y install epel-release
RUN yum -y install libaio numactl gnupg openssl
RUN yum -y update
# install gosu
RUN gpg --keyserver pool.sks-keyservers.net --recv-keys B42F6819007F00F88E364FD4036A9C25BF357DD4 \
    && curl -o /usr/local/bin/gosu -SL "https://github.com/tianon/gosu/releases/download/1.2/gosu-amd64" \
    && curl -o /usr/local/bin/gosu.asc -SL "https://github.com/tianon/gosu/releases/download/1.2/gosu-amd64.asc" \
    && gpg --verify /usr/local/bin/gosu.asc \
    && rm /usr/local/bin/gosu.asc \
    && rm -r /root/.gnupg/ \
    && chmod +x /usr/local/bin/gosu

ADD mysql-${MYSQL_VERSION}-linux-glibc2.12-x86_64.tar.gz /usr/local/
RUN ln -s /usr/local/mysql-${MYSQL_VERSION}-linux-glibc2.12-x86_64 /usr/local/mysql
ENV PATH /usr/local/mysql/bin:$PATH

WORKDIR /usr/local/mysql/
RUN mkdir data
RUN chmod 750 data
#RUN mysqld --initialize-insecure --user=mysql

VOLUME /usr/local/mysql/
ADD docker-entrypoint.sh /usr/local/mysql/
RUN chmod +x /usr/local/mysql/docker-entrypoint.sh
ENTRYPOINT ["/usr/local/mysql/docker-entrypoint.sh"]

EXPOSE 3306
WORKDIR /
CMD ["mysqld"]
