# This create hadoop
# Version 1
# Author: Jason <cooljason0404@gmail.com>

# CentOS
FROM centos:7

MAINTAINER Jason

ENV HADOOP_VERSION=2.7.2 \
    JDK_VERSION=7u79 \
    APACHE_ANT_VERSION=1.9.9 \
    APACHE_MAVEN_VERSION=3.0.5 \
    PROTOBUF_VERSION=2.5.0
    
ADD hadoop-${HADOOP_VERSION}-src.tar.gz /usr/local/
ADD jdk-${JDK_VERSION}-linux-x64.gz /usr/local/
ADD apache-ant-${APACHE_ANT_VERSION}-bin.tar.gz /usr/local/
ADD apache-maven-${APACHE_MAVEN_VERSION}-bin.tar.gz /usr/local/
ADD protobuf-${PROTOBUF_VERSION}.tar.gz /usr/local/

RUN ln -sf /usr/local/ /usr/local/jdk
RUN ln -sf /usr/local/ /usr/local/apache-maven
RUN ln -sf /usr/local/ /usr/local/apache-ant

RUN echo "#JAVA_DIR">>/etc/profile
RUN echo "export PATH=$PATH:/usr/local/jdk/bin">>/etc/profile
RUN echo "#APACHE_MAVEN_DIR">>/etc/profile
RUN echo "export PATH=$PATH:/usr/local/apache-maven/bin">>/etc/profile
RUN echo "#APACHE_ANT_DIR">>/etc/profile
RUN echo "export PATH=$PATH:/usr/local/apache-ant/bin">>/etc/profile

RUN yum update && install -y wget glibc-headers gcc-c++ openssl-devel ncurses-devel make cmake
# cmake 3.0.0版以上