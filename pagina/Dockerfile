FROM openshift/base-centos7
MAINTAINER Jose Moreno
RUN yum install httpd -y
RUN yum install epel-release -y
RUN yum install python-pip -y
RUN pip install flask
RUN yum install mod_wsgi -y
#RUN echo "WSGIScriptAlias / /var/www/proyecto/application.wsgi <VirtualHost *> ServerName www.servicios.com <Directory /var/www/proyecto/> Order deny,allow Allow from all </Directory> </VirtualHost>" > /etc/httpd/conf/httpd.conf
COPY httpd.conf/ /etc/httpd/conf/
WORKDIR /var/www/my-project/app/templates
COPY my-project/ /var/www/my-project
COPY my-project/app /var/www/my-project/app
COPY my-project/app/templates /var/www/my-project/templates
RUN chmod -R 777 /var/www
#COPY httpd.conf/ /etc/httpd/conf/
EXPOSE 80
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
