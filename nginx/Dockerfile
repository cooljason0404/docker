# This create nginx
# Version 1
# Author: Jason <cooljason0404@gmail.com>

# CentOS
FROM centos:7
MAINTAINER Jason

ENV NGINX_VERSION=1.15.8

RUN yum -y install epel-release
RUN yum -y upgrade
RUN yum -y install gcc pcre pcre-devel zlib zlib-devel openssl openssl-devel tar net-tools
RUN groupadd www
RUN useradd -g www www

RUN mkdir -p /var/install/

ADD nginx-${NGINX_VERSION}.tar.gz /var/install/

WORKDIR /var/install/nginx-${NGINX_VERSION}
RUN ./configure --user=www --group=www --prefix=/usr/local/nginx-${NGINX_VERSION} \
    --with-http_stub_status_module \
    --with-http_ssl_module \
    --with-http_realip_module \
    --with-pcre \
    --with-http_sub_module \
    --with-http_gzip_static_module
RUN make && make install

RUN ln -sf /usr/local/nginx-${NGINX_VERSION}/ /usr/local/nginx
ADD /config/nginx.conf /usr/local/nginx/conf/
RUN echo "daemon off;">>/usr/local/nginx/conf/nginx.conf
RUN echo "fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;">>/usr/local/nginx/conf/fastcgi_params

ENV PATH /usr/local/nginx/sbin:$PATH
EXPOSE 80
STOPSIGNAL SIGTERM

WORKDIR /
CMD ["nginx"]