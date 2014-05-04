FROM ubuntu:precise
MAINTAINER Nicolas Vellon <nvellon@gmail.com>

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get upgrade

RUN locale-gen en_US.UTF-8
ENV LANG       en_US.UTF-8
ENV LC_ALL     en_US.UTF-8

ADD http://cache.ruby-lang.org/pub/ruby/2.0/ruby-2.0.0-p451.tar.gz /tmp/
RUN apt-get -y install build-essential zlib1g-dev libssl-dev libreadline6-dev libyaml-dev

RUN tar -xzf /tmp/ruby-2.0.0-p451.tar.gz
RUN cd ruby-2.0.0-p451/ && ./configure --disable-install-doc && make && make install
RUN rm -rf ruby-2.0.0-p451/
RUN rm -f /tmp/ruby-2.0.0-p451.tar.gz
