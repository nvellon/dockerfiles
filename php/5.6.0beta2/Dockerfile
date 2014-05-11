FROM nvellon/base

MAINTAINER Nicolas Vellon <nvellon@gmail.com>

RUN sudo apt-get update
RUN sudo apt-get install -y build-essential libcurl4-openssl-dev autoconf libpcre3 libpcre3-dev
RUN sudo apt-get install -y libsqlite3-dev sqlite3 libmysqlclient-dev libreadline-dev libzip-dev libxslt1-dev
RUN sudo apt-get install -y libicu-dev libmcrypt-dev libmhash-dev libpcre3-dev libjpeg-dev libpng12-dev libfreetype6-dev libbz2-dev libxpm-dev

ENV SRC_PATH /tmp/php-5.6.0beta2
ENV DST_PATH /usr/local/php

RUN ln -s /usr/lib/x86_64-linux-gnu/libpcre.a /usr/lib/libpcre.a
RUN ln -s /usr/lib/x86_64-linux-gnu/libpcre.so /usr/lib/libpcre.so

# Download source
RUN cd /tmp && wget http://downloads.php.net/tyrael/php-5.6.0beta2.tar.gz && tar -xzf php-5.6.0beta2.tar.gz

# Build
ENV PHP_CONF --prefix=$DST_PATH --with-config-file-path=$DST_PATH --with-config-file-scan-dir=$DST_PATH/conf.d --config-cache --localstatedir=/var --with-layout=GNU --disable-rpath
ENV EXT_CONF --enable-mbstring --enable-mbregex --enable-phar --enable-posix --enable-soap --enable-sockets --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-zip --enable-inline-optimization --enable-intl --with-icu-dir=/usr --with-curl=/usr/bin --with-gd --with-jpeg-dir=/usr --with-png-dir=shared,/usr --with-xpm-dir=/usr --with-freetype-dir=/usr --with-bz2=/usr --with-gettext --with-iconv-dir=/usr --with-mcrypt=/usr --with-mhash --with-zlib-dir=/usr --with-regex=php --with-pcre-regex=/usr --with-openssl --with-openssl-dir=/usr/bin --with-mysql-sock=/var/run/mysqld/mysqld.sock --with-mysqli=mysqlnd --with-sqlite3=/usr --with-pdo-mysql=mysqlnd --with-pdo-sqlite=/usr
RUN mkdir $DST_PATH && cd $SRC_PATH && ./buildconf --force && ./configure $PHP_CONF --disable-cgi --with-readline --enable-pcntl --enable-cli --with-pear $EXT_CONF && make && make install
ENV PATH $PATH:/usr/local/php/bin

# Composer
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

# XDebug
RUN cd /tmp && wget https://github.com/xdebug/xdebug/archive/xdebug_2_2.zip && unzip xdebug_2_2.zip
RUN cd /tmp/xdebug-xdebug_2_2 && phpize && ./configure --enable-xdebug && make
RUN cp /tmp/xdebug-xdebug_2_2/modules/xdebug.so $DST_PATH/lib/php/xdebug.so
RUN echo "zend_extension=$DST_PATH/lib/php/xdebug.so" >> $DST_PATH/lib/php.ini

# PHPUnit
RUN cd /usr/local/bin/ && wget https://phar.phpunit.de/phpunit.phar && chmod +x phpunit.phar && mv phpunit.phar phpunit

# PHP Code Sniffer
RUN composer global require 'squizlabs/php_codesniffer=*'
RUN ln -s /.composer/vendor/squizlabs/php_codesniffer/scripts/phpcs /usr/bin/phpcs