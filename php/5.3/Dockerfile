FROM        nvellon/ubuntu_14_04

MAINTAINER  Nicolas Vellon <nvellon@gmail.com>

#
# Requirements
#
RUN     apt-get update
RUN     apt-get install -y libcurl4-openssl-dev libpcre3 libpcre3-dev libsqlite3-dev sqlite3 libmysqlclient-dev libreadline-dev libzip-dev libxslt1-dev libicu-dev libmcrypt-dev libmhash-dev libpcre3-dev libjpeg-dev libpng12-dev libfreetype6-dev libbz2-dev libxpm-dev autoconf2.13 re2c
RUN     cd /tmp && wget https://launchpad.net/ubuntu/+source/bison/1:2.5.dfsg-2.1build1/+build/3868953/+files/libbison-dev_2.5.dfsg-2.1build1_amd64.deb && dpkg -i libbison-dev_2.5.dfsg-2.1build1_amd64.deb && rm libbison-dev_2.5.dfsg-2.1build1_amd64.deb
RUN     cd /tmp && wget https://launchpad.net/ubuntu/+source/bison/1:2.5.dfsg-2.1build1/+build/3868953/+files/bison_2.5.dfsg-2.1build1_amd64.deb && dpkg -i bison_2.5.dfsg-2.1build1_amd64.deb && rm bison_2.5.dfsg-2.1build1_amd64.deb


ENV     SRC_PATH /tmp/php-5.3.28
ENV     DST_PATH /usr/local/php

#
# Download source
#
RUN     cd /tmp && wget -O php-5.3.28.tar.gz http://ar2.php.net/get/php-5.3.28.tar.gz/from/this/mirror && tar -xzf php-5.3.28.tar.gz

RUN     ln -s /usr/lib/x86_64-linux-gnu/libpcre.a /usr/lib/libpcre.a
RUN     ln -s /usr/lib/x86_64-linux-gnu/libpcre.so /usr/lib/libpcre.so
RUN     ln -s /usr/lib/x86_64-linux-gnu/libXpm.a /usr/lib/libXpm.a
RUN     ln -s /usr/lib/x86_64-linux-gnu/libXpm.so /usr/lib/libXpm.so
RUN     mkdir /usr/include/freetype2/freetype && ln -s /usr/include/freetype2/freetype.h /usr/include/freetype2/freetype/freetype.h

#
# Build
#
ENV     PHP_CONF    --prefix=$DST_PATH \
                    --with-config-file-path=$DST_PATH \
#                    --with-config-file-scan-dir=$DST_PATH/conf.d \
#                    --localstatedir=/var \
#                    --with-layout=GNU \
                    --disable-rpath \
                    --enable-mbstring \
                    --enable-mbregex \
                    --enable-phar \
                    --enable-posix \
#                    --enable-soap \
                    --enable-sockets \
                    --enable-sysvmsg \
                    --enable-sysvsem \
                    --enable-sysvshm \
                    --enable-zip \
                    --enable-inline-optimization \
                    --enable-intl \
#                    --with-icu-dir=/usr \
                    --with-curl=/usr/bin \
                    --with-gd \
#                    --with-jpeg-dir=/usr \
#                    --with-png-dir=shared,/usr \
#                    --with-xpm-dir=/usr \
                    --with-libdir=lib \
#                    --with-freetype-dir=/usr \
#                    --with-bz2=/usr \
                    --with-gettext \
#                    --with-iconv-dir=/usr \
                    --with-mcrypt=/usr \
                    --with-mhash \
                    --with-zlib-dir=/usr \
                    --with-regex=php \
                    --with-pcre-regex=/usr \
                    --with-openssl \
                    --with-openssl-dir=/usr/bin \
                    --with-mysql-sock=/var/run/mysqld/mysqld.sock \
                    --with-mysqli=mysqlnd \
                    --with-sqlite3=/usr \
                    --with-pdo-mysql=mysqlnd \
                    --with-pdo-sqlite=/usr \
                    --disable-cgi \
                    --with-readline \
                    --enable-pcntl \
                    --enable-cli \
                    --with-pear

RUN     mkdir $DST_PATH && \
        cd $SRC_PATH && \
        ./buildconf --force && \
        ./configure $PHP_CONF && \
        make && \
        make install

ENV     PATH        $PATH:/usr/local/php/bin

# Composer
#RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

# XDebug
#RUN cd /tmp && wget https://github.com/xdebug/xdebug/archive/xdebug_2_2.zip && unzip xdebug_2_2.zip
#RUN cd /tmp/xdebug-xdebug_2_2 && phpize && ./configure --enable-xdebug && make
#RUN cp /tmp/xdebug-xdebug_2_2/modules/xdebug.so $DST_PATH/lib/php/xdebug.so
#RUN echo "zend_extension=$DST_PATH/lib/php/xdebug.so" >> $DST_PATH/lib/php.ini

# PHP Code Sniffer
#RUN composer global require 'squizlabs/php_codesniffer=*'