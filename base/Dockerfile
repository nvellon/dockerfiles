FROM ubuntu

MAINTAINER Nicolas Vellon <nvellon@gmail.com>

RUN locale-gen en_US.UTF-8
ENV LANG       en_US.UTF-8
ENV LC_ALL     en_US.UTF-8

RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get -y install build-essential zlib1g-dev libssl-dev libreadline6-dev libyaml-dev wget unzip git curl
RUN apt-get -y install subversion