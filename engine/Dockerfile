FROM centos:6
MAINTAINER rui santos <ruirtsantos@gmail.com> @s4ntos

RUN yum -y install wget openssh-clients nc httpd
RUN wget http://yum.centreon.com/standard/3.0/stable/ces-standard.repo -O /etc/yum.repos.d/ces-standard.repo
# Update CentOS 
RUN yum -y update
ADD RPM-GPG-KEY-CES /etc/pki/rpm-gpg/RPM-GPG-KEY-CES
RUN yum -y install httpd \
   && sed -ri \
		-e 's!^(\s*CustomLog)\s+\S+!\1 /proc/self/fd/1!g' \
		-e 's!^(\s*ErrorLog)\s+\S+!\1 /proc/self/fd/2!g' \
        "/etc/httpd/conf/httpd.conf"
RUN yum -y install centreon-base-config-centreon-engine centreon 
RUN echo "date.timezone = Europe/London" > /etc/php.d/php-timezone.ini

# Install and configure supervisor
RUN yum -y install python-setuptools 
RUN easy_install supervisor

# Todo better split file
ADD supervisord.conf /etc/supervisord.conf
# File to be used after configuration
ADD supervisord_2.conf /etc/supervisord_2.conf

# Expose port HTTP for the service
EXPOSE 80

CMD  ["/usr/bin/supervisord","--configuration=/etc/supervisord.conf"]