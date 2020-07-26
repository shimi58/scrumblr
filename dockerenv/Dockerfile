FROM centos:centos7

# http://wordpress.ideacompo.com/?p=13878
# 上記を参考に環境のベースを構築
# 起動方法
# 

# Import the Centos-7 RPM GPG key to prevent warnings
RUN rpm --import http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-7
RUN rpm --import http://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-7

# system update
RUN yum -y update && yum clean all

# set locale
RUN yum reinstall -y glibc-common && yum clean all
RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV LC_ALL ja_JP.UTF-8
RUN unlink /etc/localtime
RUN ln -s /usr/share/zoneinfo/Japan /etc/localtime

# rootパスワード設定
RUN echo "root:root" | chpasswd

# =====
# BASE packages
# =====
RUN yum --enablerepo=extras clean metadata
RUN yum install -y  openssl openssl-devel 
RUN yum install -y openssh openssh-server
RUN yum install -y net-tools wget sudo
RUN yum install -y tar zip unzip  which tree
RUN yum install -y git
# radis構築に必要
RUN yum install -y  make gcc gcc-c++

# =====
# Service
# =====

# 初期構築Shell起動用サービスを登録
COPY ./docker_data/autorun.service /etc/systemd/system/

RUN systemctl enable autorun.service
