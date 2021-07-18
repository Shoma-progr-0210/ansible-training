FROM centos:7

# system update
RUN yum -y update && yum clean all

# # set locale
# RUN yum update -y glibc-common && \
# yum clean all
# ENV LANG ja_JP.UTF-8
# ENV LANGUAGE ja_JP:ja
# ENV LC_ALL ja_JP.UTF-8
# RUN unlink /etc/localtime
# RUN ln -s /usr/share/zoneinfo/Japan /etc/localtime

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