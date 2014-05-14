FROM nvellon/base

MAINTAINER Nicolas Vellon <nvellon@gmail.com>

RUN sudo apt-get update
RUN sudo apt-get install -y libcurl4-openssl-dev autoconf libpcre3 libpcre3-dev re2c
RUN sudo apt-get install -y libsqlite3-dev sqlite3 libmysqlclient-dev libreadline-dev libzip-dev libxslt1-dev
RUN sudo apt-get install -y libicu-dev libmcrypt-dev libmhash-dev libpcre3-dev libjpeg-dev libpng12-dev libfreetype6-dev libbz2-dev libxpm-dev
RUN cd /tmp && wget https://launchpad.net/ubuntu/+source/bison/2:2.7.1.dfsg-1/+build/4586386/+files/libbison-dev_2.7.1.dfsg-1_amd64.deb && dpkg -i libbison-dev_2.7.1.dfsg-1_amd64.deb && rm libbison-dev_2.7.1.dfsg-1_amd64.deb
RUN cd /tmp && wget https://launchpad.net/ubuntu/+source/bison/2:2.7.1.dfsg-1/+build/4586386/+files/bison_2.7.1.dfsg-1_amd64.deb && dpkg -i bison_2.7.1.dfsg-1_amd64.deb && rm bison_2.7.1.dfsg-1_amd64.deb 

ENV SRC_PATH /usr/src/php-src
ENV DST_PATH /usr/local/php

RUN ln -s /usr/lib/x86_64-linux-gnu/libpcre.a /usr/lib/libpcre.a
RUN ln -s /usr/lib/x86_64-linux-gnu/libpcre.so /usr/lib/libpcre.so

# Clone PHP
RUN cd /usr/src && git clone https://github.com/php/php-src.git

# Clone xdebug
RUN cd /usr/src && git clone https://github.com/xdebug/xdebug.git

# Clone PHPUnit
RUN cd /usr/src && git clone https://github.com/sebastianbergmann/phpunit.git

# Clone PHP Code Sniffer
RUN cd /usr/src && git clone https://github.com/squizlabs/PHP_CodeSniffer.git