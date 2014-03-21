FROM ubuntu:13.10
MAINTAINER hyone "hyone.development@gmail.com"

## user
# RUN echo 'root:root' | chpasswd

## repository setup
RUN echo "deb http://jp.archive.ubuntu.com/ubuntu saucy main restricted universe" > /etc/apt/sources.list ; \
    echo "deb http://jp.archive.ubuntu.com/ubuntu saucy-updates main restricted universe" >> /etc/apt/sources.list ; \
    echo "deb http://security.ubuntu.com/ubuntu saucy-security main restricted universe" >> /etc/apt/sources.list

## packages

ENV DEBIAN_FRONTEND noninteractive

# avoid complaining from installing upstart
# see: https://github.com/dotcloud/docker/issues/1724#issuecomment-34406469
RUN apt-mark hold initscripts udev plymouth mountall ; \
    dpkg-divert --local --rename --add /sbin/initctl \
      && ln -sf /bin/true /sbin/initctl \
      && ln -sf /bin/false /usr/sbin/policy-rc.d ; \
    apt-get update ; \
    apt-get upgrade -y
# RUN dpkg-divert --local --rename /usr/bin/ischroot && ln -sf /bin/true /usr/bin/ischroot

# base package
RUN apt-get install -y \
  curl \
  net-tools \
  wget \
  build-essential \
  autoconf \
  bison \
  flex \
  make

# base settings
RUN locale-gen ja_JP.UTF-8 ; \
    echo 'Asia/Tokyo' > /etc/timezone ; \
    /usr/sbin/dpkg-reconfigure -f noninteractive tzdata

## Command
CMD ["/bin/bash"]
