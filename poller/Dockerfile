FROM centos:6
MAINTAINER rui santos <ruirtsantos@gmail.com> @s4ntos

RUN yum -y install wget openssh-server sudo openssh-clients nc
RUN wget http://yum.centreon.com/standard/3.0/stable/ces-standard.repo -O /etc/yum.repos.d/ces-standard.repo
# Update CentOS 
RUN yum -y update
ADD ./RPM-GPG-KEY-CES /etc/pki/rpm-gpg/RPM-GPG-KEY-CES
RUN yum -y install centreon-poller-centreon-engine

# Install and configure supervisor
RUN yum -y install python-setuptools 
RUN easy_install supervisor

# Todo better split file
ADD supervisord.conf /etc/supervisord.conf
