FROM        nvellon/ubuntu_14_04

MAINTAINER  Nicolas Vellon <nvellon@gmail.com>

#
# Paths
#

ENV     SRC_PATH /tmp/php-5.4.29
ENV     DST_PATH /usr/local/php


#
# Requirements
#

RUN     apt-get update

RUN     apt-get install -y \
                libcurl4-openssl-dev \
                libpcre3 \
                libpcre3-dev \
                libsqlite3-dev \
                sqlite3 \
                libmysqlclient-dev \
                libreadline-dev \
                libzip-dev \
                libxslt1-dev \
                libicu-dev \
                libmcrypt-dev \
                libmhash-dev \
                libjpeg-dev \
                libpng12-dev \
                libfreetype6-dev \
                libbz2-dev \
                libxpm-dev \
                autoconf2.13 \
                re2c


RUN     cd /tmp && \
        wget https://launchpad.net/ubuntu/+source/bison/1:2.5.dfsg-2.1build1/+build/3868953/+files/libbison-dev_2.5.dfsg-2.1build1_amd64.deb && \
        dpkg -i libbison-dev_2.5.dfsg-2.1build1_amd64.deb && \
        rm libbison-dev_2.5.dfsg-2.1build1_amd64.deb

RUN     cd /tmp && \
        wget https://launchpad.net/ubuntu/+source/bison/1:2.5.dfsg-2.1build1/+build/3868953/+files/bison_2.5.dfsg-2.1build1_amd64.deb && \
        dpkg -i bison_2.5.dfsg-2.1build1_amd64.deb && \
        rm bison_2.5.dfsg-2.1build1_amd64.deb

RUN     ln -s /usr/lib/x86_64-linux-gnu/libpcre.a /usr/lib/libpcre.a
RUN     ln -s /usr/lib/x86_64-linux-gnu/libpcre.so /usr/lib/libpcre.so

RUN     ln -s /usr/lib/x86_64-linux-gnu/libXpm.a /usr/lib/libXpm.a
RUN     ln -s /usr/lib/x86_64-linux-gnu/libXpm.so /usr/lib/libXpm.so


#
# Download source
#

RUN     cd /tmp && \
        wget -O php-5.4.29.tar.gz http://ar2.php.net/get/php-5.4.29.tar.gz/from/this/mirror && \
        tar -xzf php-5.4.29.tar.gz


#
# Build
#

ENV     PHP_CONF    --prefix=$DST_PATH \
                    --with-config-file-path=$DST_PATH \
                    --enable-mbstring \
                    --enable-mbregex \
                    --enable-phar \
                    --enable-posix \
                    --enable-sockets \
                    --enable-sysvmsg \
                    --enable-sysvsem \
                    --enable-sysvshm \
                    --enable-zip \
                    --enable-inline-optimization \
                    --enable-intl \
                    --with-curl=/usr/bin \
                    --with-gd \
                    --with-libdir=lib \
                    --with-bz2=/usr \
                    --with-gettext \
                    --with-mcrypt=/usr \
                    --with-mhash \
                    --with-zlib-dir=/usr \
                    --with-regex=php \
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
                    --with-pear \
                    --enable-libgcc

RUN     mkdir $DST_PATH && \
        cd $SRC_PATH && \
        ./buildconf --force && \
        ./configure $PHP_CONF && \
        make && \
        make install

ENV     PATH    $PATH:/usr/local/php/bin

RUN     cp $SRC_PATH/php.ini-development $DST_PATH/lib/php.ini

#
# OpCache
#

RUN     pecl install -f zendopcache

RUN     echo "" >> /usr/local/php/lib/php.ini

RUN     echo "zend_extension=/usr/local/php/lib/php/extensions/no-debug-non-zts-20100525/opcache.so" >> /usr/local/php/lib/php.ini

RUN     echo "" >> /usr/local/php/lib/php.ini

RUN     echo "opcache.memory_consumption=128"       >> /usr/local/php/lib/php.ini
RUN     echo "opcache.interned_strings_buffer=8"    >> /usr/local/php/lib/php.ini
RUN     echo "opcache.max_accelerated_files=4000"   >> /usr/local/php/lib/php.ini
RUN     echo "opcache.revalidate_freq=60"           >> /usr/local/php/lib/php.ini
RUN     echo "opcache.fast_shutdown=1"              >> /usr/local/php/lib/php.ini
RUN     echo "opcache.enable_cli=1"                 >> /usr/local/php/lib/php.ini


#
# XDebug
#

RUN     cd /tmp && \
        wget https://github.com/xdebug/xdebug/archive/xdebug_2_2.zip && \
        unzip xdebug_2_2.zip && \
        cd xdebug-xdebug_2_2 && \
        phpize && \
        ./configure --enable-xdebug && \
        make

RUN     cp /tmp/xdebug-xdebug_2_2/modules/xdebug.so $DST_PATH/lib/php/xdebug.so

RUN     echo "zend_extension=$DST_PATH/lib/php/xdebug.so" >> $DST_PATH/lib/php.ini


#
# Composer
#

RUN     curl -sS https://getcomposer.org/installer | php && \
        mv composer.phar /usr/local/bin/composer

RUN     mkdir $DST_PATH/lib/php/composer

ENV     COMPOSER_HOME   $DST_PATH/lib/php/composer

ENV     PATH    $PATH:/usr/local/php/lib/php/composer/vendor/bin


#
# PHP Code Sniffer
#

RUN composer global require 'squizlabs/php_codesniffer=*'


#
# PHPUnit
#

RUN composer global require 'phpunit/phpunit=*'