FROM centos:centos7
LABEL maintainer="prabhatiitbhu@gmail.com"

# Install NGINX
RUN yum -y update; yum clean all
RUN yum -y install http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm; yum -y makecache
RUN yum -y install nginx-1.10.1

# Remove default files we don't need
RUN rm /etc/nginx/conf.d/default.conf

# Add default configuration
COPY conf/nodejs.conf /etc/nginx/conf.d/nodejs.conf
COPY conf/nginx.conf /etc/nginx/nginx.conf
COPY my-site.com.crt /etc/nginx/my-site.com.crt
COPY my-site.com.key /etc/nginx/my-site.com.key

EXPOSE 80

CMD ["nginx"]
