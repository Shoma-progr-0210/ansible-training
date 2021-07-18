# CentOS7
FROM centos:7

# system update
RUN yum -y update && yum clean all

# install sudo
RUN yum -y install sudo
# install ssh clients
RUN yum -y install openssh-clients

# install ansible
RUN yum -y install epel-release && \
yum -y install ansible && \
yum clean all

# setttings
ADD ansible.cfg /etc/ansible