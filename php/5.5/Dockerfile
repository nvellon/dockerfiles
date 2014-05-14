FROM nvellon/php-base

MAINTAINER Nicolas Vellon <nvellon@gmail.com>

# Variables en nvellon/php-base
# ENV SRC_PATH /usr/src/php-src
# ENV DST_PATH /usr/local/php

# PHP
RUN cd /usr/src/php-src && git checkout PHP-5.5
ENV PHP_CONF --prefix=$DST_PATH --with-config-file-path=$DST_PATH --with-config-file-scan-dir=$DST_PATH/conf.d --config-cache --localstatedir=/var --with-layout=GNU --disable-rpath
ENV EXT_CONF --enable-mbstring --enable-mbregex --enable-phar --enable-posix --enable-soap --enable-sockets --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-zip --enable-inline-optimization --enable-intl --with-icu-dir=/usr --with-curl=/usr/bin --with-gd --with-jpeg-dir=/usr --with-png-dir=shared,/usr --with-xpm-dir=/usr --with-freetype-dir=/usr --with-bz2=/usr --with-gettext --with-iconv-dir=/usr --with-mcrypt=/usr --with-mhash --with-zlib-dir=/usr --with-regex=php --with-pcre-regex=/usr --with-openssl --with-openssl-dir=/usr/bin --with-mysql-sock=/var/run/mysqld/mysqld.sock --with-mysqli=mysqlnd --with-sqlite3=/usr --with-pdo-mysql=mysqlnd --with-pdo-sqlite=/usr
RUN mkdir $DST_PATH && cd $SRC_PATH && ./buildconf --force && ./configure $PHP_CONF --disable-cgi --with-readline --enable-pcntl --enable-cli --with-pear $EXT_CONF && make && make install
ENV PATH $PATH:$DST_PATH/bin

# XDebug
RUN cd /usr/src/xdebug && git checkout xdebug_2_2 && phpize && ./configure --enable-xdebug && make
RUN cp /usr/src/xdebug/modules/xdebug.so $DST_PATH/lib/php/xdebug.so
RUN echo "zend_extension=$DST_PATH/lib/php/xdebug.so" >> $DST_PATH/lib/php.ini

# Composer
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer
#RUN composer self-update

# PHPUnit
RUN cd /usr/src/phpunit && git checkout 4.1 && composer install
RUN ln -s /usr/src/phpunit/phpunit /usr/local/bin/phpunit

# PHP Code Sniffer
RUN cd /usr/src/PHP_CodeSniffer && git checkout master && composer install
RUN ln -s /usr/src/PHP_CodeSniffer/scripts/phpcs /usr/local/bin/phpcs