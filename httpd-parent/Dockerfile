FROM registry.access.redhat.com/ubi8/ubi:8.0

MAINTAINER Red Hat Training <training@redhat.com>

# DocumentRoot for Apache
ENV DOCROOT=/var/www/html 


RUN   yum install -y --nodocs --disableplugin=subscription-manager httpd && \
yum clean all --disableplugin=subscription-manager -y && \
echo "Hello from the httpd container!" > ${DOCROOT}/index.html

# Allows child images to inject their own content into DocumentRoot
COPY htdocs/ ${DOCROOT}/
ONBUILD COPY htdocs/ ${DOCROOT}/

EXPOSE 80

# Launch httpd
CMD /usr/sbin/httpd -DFOREGROUND
